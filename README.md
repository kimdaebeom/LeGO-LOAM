# LeGO-LOAM
## How to use OS0-128 with LeGO-LOAM

Upper file is LeGO-LOAM forked file.

First of all, you have to edit the utility.h in include file.
Change topic name of pointcloud2 type message.
~~~
// extern const string pointCloudTopic = "/velodyne_points";
extern const string pointCloudTopic = "/os_cloud_node/points";
~~~

Modify useCloudRing value.
~~~
extern const bool useCloudRing = false; // if true, ang_res_y and ang_bottom are not used
~~~

Add parameters of OS1-128.
~~~
// Ouster OS0-128
extern const string LIDAR_TYPE = "Ouster OS0-128";
extern const int N_SCAN = 128;
extern const int Horizon_SCAN = 1024; //2048
extern const float ang_res_x = 360.0/float(Horizon_SCAN);
extern const float ang_res_y = 90.0/float(N_SCAN-1); //45
extern const float ang_bottom = 22.5+0.1; //22.5
extern const int groundScanInd = 30;
~~~

Lastly, you have to edit ImageProjection.cpp in source file.
uncomment the line of 166.
~~~
cloudHeader.stamp = ros::Time::now(); // Ouster lidar users may need to uncomment this line
~~~

With ROS bag file, Ouster launch, and LeGO-LOAM run.launch file, you can use LeGO-LOAM with your OS1-128 dataset.

</br>

- Add parameters of HDL-64E for KITTI dataset.
~~~
// HDL-64E
extern const int N_SCAN = 64;
extern const int Horizon_SCAN = 1800;
extern const float ang_res_x = 360.0/float(Horizon_SCAN);
extern const float ang_res_y = 26.9/float(N_SCAN-1);
extern const float ang_bottom = 25;
extern const int groundScanInd = 30;
~~~
