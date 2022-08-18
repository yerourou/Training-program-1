# Training-program-1
项目1
#include<opencv2/highgui.hpp>
#include<opencv2/imgproc.hpp>
#include<opencv2/imgcodecs.hpp>
#include<iostream>
using namespace std;
using namespace cv;
int main()
{
	Mat img = imread("C:/Users/86181/Desktop/program1/creditcard01.png");
	imshow("原始图像", img);
	Mat imgGray;
	cvtColor(img, imgGray, COLOR_BGR2GRAY);
	imshow("灰度图像", imgGray);
	Mat imgGray_threshold;
	threshold(imgGray, imgGray_threshold, 100, 255, THRESH_BINARY);
	imshow("二值化图像", imgGray_threshold);
	vector<vector<Point>> contours;
	vector<Vec4i> hierarchy;
	findContours(imgGray_threshold, contours, hierarchy, RETR_TREE, CHAIN_APPROX_SIMPLE, Point());
	//绘制轮廓
	drawContours(img, contours, -1, Scalar(0,0,255),2);
	imshow("Contours Image", img); //轮廓
	//refCnts = contours.sort_contours(contours, method = "left-to-right");
	waitKey(0);
   
}
