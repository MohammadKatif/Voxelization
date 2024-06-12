# Voxelization
Voxelization is really important process in computer science for converting 3D models into a discrete grid format and subsequently into arrays, enabling efficient analysis, rendering, and processing in various applications such as medical imaging, scientific simulations, computer graphics, etc. However, when I was trying to learn how to perform voxelization for a personal project, I was unable to find a useful tutorial for doing so. 
Therefore, in this code I have performed voxelization in python to convert 3D objects to 3D voxel grids and then to 3D voxel arrays using 3 python libraries: trimesh, matplotlib and numpy.

## Dataset:
For the 3D object, I have used a airplane 3D CAD model known as 'airplane_0001.off' from the [ModelNet40 Dataset](https://www.kaggle.com/datasets/balraj98/modelnet40-princeton-3d-object-dataset), which is a princeton 3D object dataset. Although there are are 12,311 3D objects in this dataset, I have only used one of the 3D object to demonstrate the process of voxelization

## Process:
**First**, I have loaded the 3D mesh model of the airplane using the code: ```mesh = trimesh.load_mesh('airplane_0001.off')``` . (I downloaded and stored the 3D model directly from the ModelNet40 dataset into my working directory beforehand)
This 3D mesh model can be visualized using ```mesh.show()``` :
![image](https://github.com/MohammadKatif/Voxelization/assets/143898427/569a329b-3671-4997-9db0-22776f292614)

**After that**, I have performed voxelization on the 3D mesh model (with a pitch value of 1.0) by converting it to a voxel grid and then to a voxel array.

**Lastly**, for confirming whether the voxelization process was successful, I have plotted the 3D object in matplotlib using the voxel array.
![image](https://github.com/MohammadKatif/Voxelization/assets/143898427/1be56a11-2917-4e12-a74c-bcfd35b08ebf)
