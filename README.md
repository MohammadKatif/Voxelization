# Voxelization
Voxelization is a crucial process in computer science for converting 3D models into a discrete voxel grid format and subsequently into arrays, enabling efficient analysis, rendering, and processing in various applications such as medical imaging, scientific simulations, computer graphics, etc. However, when I was trying to learn how to perform voxelization for a personal project, I was unable to find a useful tutorial for doing so.
Therefore, in this code, I have performed voxelization in Python to convert 3D objects to 3D voxel grids and then to 3D voxel arrays using 2 Python libraries: Trimesh and Open3d.

## Dataset:
For the 3D object, I have used an airplane 3D CAD model known as 'airplane_0001.off' from the [ModelNet40 Dataset](https://www.kaggle.com/datasets/balraj98/modelnet40-princeton-3d-object-dataset), which is a Princeton 3D object dataset. Although there are 12,311 3D objects in this dataset, I have only used one of the 3D objects to demonstrate the process of voxelization.

## Voxelization using trimesh library:
**First**, I loaded the 3D mesh model of the airplane using the code: ```mesh = trimesh.load_mesh('airplane_0001.off')```. (I downloaded and stored the 3D model directly from the ModelNet40 dataset into my working directory beforehand)
This 3D mesh model can be visualized using ```mesh.show()```:
![image](https://github.com/MohammadKatif/Voxelization/assets/143898427/569a329b-3671-4997-9db0-22776f292614)

**After that**, I performed voxelization on the 3D mesh model (with a pitch value of 1.0) by converting it to a voxel grid using the code: ```voxel_grid = mesh.voxelized(pitch=1.0)```. Then, I converted that voxel grid into a 3D voxel array using the code: ```voxel_array = voxel_grid.matrix.astype(int)```.

**Lastly**, to confirm whether the voxelization process was successful, I plotted the voxel grid of the model 2 times. The first time, I plotted the voxel grid using the trimesh library itself. The second time, I plotted the voxel grid in matplotlib from two different perspectives (front and back) using the voxel array.

Voxel grid using trimesh:
![image](https://github.com/MohammadKatif/Voxelization/assets/143898427/6f834274-c54e-4b0b-b8a4-908675f1e8aa)

Voxel grid using matplotlib:
![image](https://github.com/MohammadKatif/Voxelization/assets/143898427/1be56a11-2917-4e12-a74c-bcfd35b08ebf)

## Voxelization using open3d library
**First**, I loaded the 3D mesh model of the airplane using the code: ```mesh = o3d.io.read_triangle_mesh('airplane_0001.off')```. (I downloaded and stored the 3D model directly from the ModelNet40 dataset into my working directory beforehand).

**After that**, I performed voxelization on the 3D mesh model (with a voxel_size value of 0.01) by converting it to a voxel grid using the code: ```voxel_grid = o3d.geometry.VoxelGrid.create_from_triangle_mesh(mesh, voxel_size=0.01)```.

**Then**, in order to convert the voxel_grid into a voxel_grid_array, I first converted the voxel_grid into a voxel_coords array and then I converted that voxel_coords array into a voxel_grid_array.

**Lastly**, to confirm whether the voxelization process was successful, I plotted the voxel grid of the model 2 times using matplotlib. The first time, I plotted the voxel grid using the voxel_coords array. The second time, I plotted the voxel grid using the voxel_grid_array. *(Unlike trimesh, the plotting mechanism of open3d doesn't seems to work in google colab, which is why I have used matplotlib to visualize the voxel grids in this section)*

Voxel grid using voxel_coords array:
![image](https://github.com/MohammadKatif/Voxelization/assets/143898427/9ee9a79d-5ce4-460c-8837-831adbc0e2ec)

Voxel grid using voxel_grid_array:
![image](https://github.com/MohammadKatif/Voxelization/assets/143898427/ea04d972-4ec6-4e90-98c3-4142910ffb94)

## Additional Information:
In this code, I have perfomed voxelization on only one mesh object using trimesh and open3d to demonstrate how the voxelization process works. However, the same method cannot be applied when it comes to voxelizing an entire 3D objects dataset(e.g. ModelNet40/10) in google colab.
