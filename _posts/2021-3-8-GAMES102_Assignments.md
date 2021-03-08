---
layout: post
title: GAMES-102 Assignment
subtitle: CODE
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [code]
---

## Assignment 1

[Original details](/assets/games_102_assignment/assignment1.md)

Notes: The method I had used in my code is motivated by  Xueyuan Yang.

My CanvasData.h was changed like below:

```c++
struct CanvasData {
	std::vector<Ubpa::pointf2> points;
	Ubpa::valf2 scrolling{ 0.f,0.f };
	bool opt_enable_grid{ true };
	bool opt_enable_context_menu{ true };
	bool adding_line{ false };

	bool hadInputDone{ false };//Onceaftering inputting all points, check this, 		which will recalculate the interpolation points.
	bool Polynomial{ false };
	bool Gauss{ false };
	bool LSM{ false };
	bool RR{ false };


	float step_length = 1.0;
	float lambda = 50.0;
	std::vector<double> IntpltnPts;
	std::vector<double> PolynomialY;
	std::vector<double> GaussY;
	std::vector<double> LSMY;
	std::vector<double> RRY;
};
```



### 1. Interpolation fitting

* Polynomial function as basis function:

  The algorithm is Lagrange interpolation algorithm.

  ```c++
  std::vector<double> Polynomial(std::vector<double> ip, CanvasData* data) {
  	std::vector<double> v;
  	for (const double p : ip) {
  		double y = 0.0;
  		for (int m = 0; m < data->points.size(); m++) {
  			double l = data->points[m][1];
  			for (int o = 0; o < data->points.size(); o++) {
  				if (m != o) {
  					l *= (p - data->points[o][0]) / (data->points[m][0] -                              data->points[o][0]);
  				}
  			}
  			y += l;
  		}
  		v.push_back(y);
  	}
  	return v;
  }
  ```

* Gauss Basis Function

  ```c++
  std::vector<double> Gauss(std::vector<double> ip, CanvasData* data) {
  	size_t dataSize = data->points.size();
  	VectorXd y(dataSize + 1);
  	MatrixXd x(dataSize + 1, dataSize + 1);
  	x.setOnes();
  	VectorXd b(dataSize + 1);
  	
  	double lmb_sq = 1 / (pow(data->lambda, 2));
  	for (size_t row = 0; row < dataSize; row++) {
  		y(row) = data->points[row][1];
  		for (size_t col = 1; col <= dataSize; col++) {
  			x(row, col) = exp(-0.5 * pow(data->points[row][0] - data->points[col-1][0], 2) * lmb_sq);
  		}
  	}
  	y(dataSize) = (data->points[dataSize - 1][1] + data->points[dataSize - 2][1]) / 2;
  	for (size_t col = 1; col <= dataSize; col++) 
  		x(dataSize, col) = exp(-0.5 * pow((data->points[dataSize - 1][0] + data->points[dataSize - 2][0]) / 2 - data->points[col-1][0], 2) * lmb_sq);
  	
  	b = x.colPivHouseholderQr().solve(y);
  	std::vector<double> v;
  	for (const double p : ip) {
  		double py = b(0);
  		for (size_t ts = 1; ts <= dataSize; ts++) {
  			py += b(ts) * exp(-0.5 * pow(p - data->points[ts-1][0], 2) * lmb_sq);
  		}
  		v.push_back(py);
  	}
  	return v;
  }
  ```

* LSM:

  

```c++
std::vector<double> LSM(std::vector<double> ip, CanvasData* data) {
	std::vector<double> v;

	size_t dataSize = data->points.size();
	size_t m = 10;
	if (m >= dataSize) m = dataSize - 3;

	VectorXd y(dataSize);
	VectorXd a(m + 1);
	MatrixXd b(dataSize, m + 1);

	for (size_t row = 0; row < dataSize; row++) {
		for (size_t col = 0; col <= m; col++) {
			b(row, col) = pow(data->points[row][0], col);
		}
		y(row) = data->points[row][1];
	}

	a = (b.transpose() * b).inverse() * (b.transpose() * y);
	
	for (const float p : ip) {
		double y = 0.0;
		for (int i = 0; i <= m; i++) {
			y += pow(p, i) * a(i);
		}
		v.push_back(y);
	}
	return v;
}

```

* RR:

  ```c++
  std::vector<double> RR(std::vector<double> ip, CanvasData* data, float lambda) {
  	std::vector<double> v;
  
  	size_t dataSize = data->points.size();
  	size_t m = 10;
  	if (m >= dataSize) m = dataSize - 3;
  
  	VectorXd y(dataSize);
  	VectorXd a(m + 1);
  	MatrixXd b(dataSize, m + 1);
  
  	for (size_t row = 0; row < dataSize; row++) {
  		for (size_t col = 0; col <= m; col++) {
  			b(row, col) = pow(data->points[row][0], col);
  		}
  		y(row) = data->points[row][1];
  	}
  
  	a = (b.transpose() * b + lambda * MatrixXd::Identity(m + 1, m + 1)).inverse() * (b.transpose() * y);
  
  	for (const float p : ip) {
  		double y = 0.0;
  		for (int i = 0; i <= m; i++) {
  			y += pow(p, i) * a(i);
  		}
  		v.push_back(y);
  	}
  	return v;
  }
  ```

  