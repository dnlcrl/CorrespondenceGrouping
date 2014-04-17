# CorrespondenceGrouping

Project based on the tutorial found at [PointClouds.org](http://pointclouds.org/documentation/tutorials/correspondence_grouping.php#correspondence-grouping)


## Usage

 1. Download the pcd data from [Github](https://raw.github.com/PointCloudLibrary/data/master/tutorials/correspondence_grouping) and extract files in a folder of your convenience.

 2. Download the repository from [Github](https://github.com/danieleciriello/CorrespondenceGrouping)
 
 3. Uncompress the archive
 
 4. Move to the uncompressed directory, and create a build directory in there:

		$ cd path/to/CorrespondenceGrouping-<branch> && mkdir build && cd build
 
 
 5. Run the Cmake build system using the default options:
 		
 		$ cmake ..
   
    Or change them:
		
		$ cmake -DCMAKE_BUILD_TYPE=Release ..

 6. Compile everything:

 		$ make
 
 7. After you have created the executable, you can then launch it following this example:

 		$ ./CorresponseGrouping milk.pcd milk_cartoon_all_small_clorox.pcd

 	Or alternatively, if you prefer specifying the radii in units of cloud resolution:

 		$ ./correspondence_grouping milk.pcd milk_cartoon_all_small_clorox.pcd milk.pcd milk_cartoon_all_small_clorox.pcd -r --model_ss 7.5 --scene_ss 20 --rf_rad 10 --descr_rad 15 --cg_size 10
	
	Remember to replace milk.pcd and milk_cartoon_all_small_clorox.pcd with model and scene filenames, in this exact order. If you want you can add other command line options as described at the beginning of [this tutorial](http://pointclouds.org/documentation/tutorials/correspondence_grouping.php#correspondence-grouping).

After a few seconds, you will see an output similar to:

	Model total points: 12575; Selected Keypoints: 686
	Scene total points: 307200; Selected Keypoints: 3747
	Correspondences found: 1777
	Model instances found: 1

	    Instance 1:
	        Correspondences belonging to this instance: 21

	            |  0.968 -0.127  0.218 |
	        R = |  0.124  0.992  0.031 |
	            | -0.220 -0.003  0.975 |

	        t = < -0.158, 0.215, -0.042 >

The output window should look like this (depending on the command line options used):

![alt tag](http://s28.postimg.org/c4nt9cjfh/Schermata_2014_04_17_alle_14_43_32.png)

## Notes

 - The CMakeLists.txt has been edited in order to let make correctly link and build on Mac OS X 10.9

 - If you are using different point clouds and you don’t know how to set the various parameters for this tutorial you can use the -r flag and try setting the LRF and descriptor radii to 5, 10, 15 or 20 times the actual cloud resolution. After that you probably will have to tweak the values by hand to achieve the best results.