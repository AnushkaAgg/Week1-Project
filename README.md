# Week1-Project
#include<opencv2/opencv.hpp>
#include<opencv2/highgui/highgui.hpp>
#include<opencv2/imgproc/imgproc.hpp>
#include<iostream>
using namespace cv;
using namespace std;
Mat rotate(Mat src, double angle)
{
	Mat dst;
	Point2f pt(src.cols / 2., src.rows / 2.);
	Mat r = getRotationMatrix2D(pt, angle, 0.7);
	warpAffine(src, dst, r, Size(src.cols, src.rows));
	return dst;
}
int main()
{
	Mat img = imread("graphic-era-logo_w.jpg");
	if (img.empty())
	{
		cout << "error..no image";
		return -1;
	}
	namedWindow("image", WINDOW_NORMAL);
	imshow("OriginalImage", img);
	Mat dst;
	double angle;
	cout << "Enter angle: ";
	cin >> angle;
	dst = rotate(img, angle);
	//Mat img1 = imread("graphic-era-logo_w.jpg", IMREAD_GRAYSCALE);
	//imshow("grayscale image", img1);
	imshow("dst", dst);
	waitKey();
	return 0;
}
