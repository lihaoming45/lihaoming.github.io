# hand interaction reconstruction with non parametric representation

[1] 2020 CVPR Weakly-Supervised Mesh-Convolutional Hand Reconstruction in the Wild

[2] 2021 CVPR Camera-Space Hand Mesh Recovery via Semantic Aggregation and Adaptive 2D-1D Registration

[3] 2021 CVPR End-to-End Human Pose and Mesh Reconstruction with Transformers

[4] 2019 PIFu Pixel-Aligned Implicit Function for High-Resolution Clothed Human Digitization 

[5] 2019 SynSin: End-to-end View Synthesis from a Single Image

[6] 2021 ICCV PyMAF 3D Human Pose and Shape Regression with Pyramidal Mesh Alignment Feedback Loop



### Motivation

#### Background

Mesh representation 

##### Non-parametric representation 

Pros:

- Relative easy to get. from point cloud to mesh(and register meshes)
- Simple and straightforward
- **In the space well aligned with images via perceptive projection or in the same space with point clouds, kind of linear mapping (in which sense?)**
- **Convolution or computation blocks on the meshes and has the potential to establish connection between inputs and outputs. For images to meshes, the computation blocks can integrate visual feature and geometry feature.**
- local deformation

Cons: 

- High DOF
- **Need to introduce constraints for high DOF**
- Convolution or computation blocks on meshes are not well studied yet.



##### Parametric representation 

Pros:

- Low dim: the mesh space is largely constrained by the low dimensional shape and pose space; no local artifacts or distortion 
- Easy for artists to control or manipulate the hand(objects) if the learned model parameters conform with artists editing habit. 

Cons:

- Not easy to learn a parametric model and not easy to learn a parametric model friendly to artists
- Highly non linear low dimensional space, e.g. rotations, hard to learn a mapping from image to it. highly non-linear mapping kind of learning an inverse kinematics mapping

##### How to learn with non-parametric reprensentation?

- mesh convolution: [1] [2] for hands. Many mesh convolutions proposed but not good enough. 
- transformer [3]

Challenges: 

- for hands, current mesh convolution, transformer networks can serve our purpose
- for objects, no available options, but there indeed exists some work using Atlasnet for objects. 

Some work proporgate image features(sparse or dense) to decoder [2,4,5,6]

### Contribution

- Attention between interaction between hands/or hand with objects (existing methods using attention or transformer in the image space, or encoder; no interaction in the decoder)
- Local dense image features propagate to the vertices/joints
- Cascade or coarse to refine in different layer of the network implicitly, in a forward network, not in an iterative feedback loop (template coarse to fine; t1= upsample(t0) and learn the residual  t1_gt-t1)
- In latter layers, attention only happens in local areas

![image-20220210140622194](C:\Users\yeqi\AppData\Roaming\Typora\typora-user-images\image-20220210140622194.png)





### ![image-20220210135426570](C:\Users\yeqi\AppData\Roaming\Typora\typora-user-images\image-20220210135426570.png)

![image-20220210135843509](C:\Users\yeqi\AppData\Roaming\Typora\typora-user-images\image-20220210135843509.png)





![image-20210902135825138](C:\Users\yeqi\AppData\Roaming\Typora\typora-user-images\image-20210902135825138.png)

