# Image Processing & Computer Vision

### Week 1

#### Pinhole Camera 

• Small pinhole gathers less light

• Larger pinhole reduces sharpness

#### Dirac Delta

![image-20201230213947033](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201230213947033.png)

$\int_{-\infty}^\infty \delta(t) dt = 1$																						$\delta(t) = \lim_{\epsilon \to 0}[y_\epsilon (t)]$

It's value zero every where except 0, which is 1							 area will be one

##### Sifting Property:

$\int_{-\infty}^\infty f(t)\delta(t)dt = f(0) \longrightarrow \int_{-\infty}^\infty f(t)\delta(t-a)dt = f(a) $ 

E.g. sampling in 2D

the value of the pixel position XY is obtained by the delta function being shifted to that position

$\int_{-\infty}^\infty\int_{-\infty}^\infty f(a,b)\delta(a-x,b-y)da\;db = f(x,y) $

#### Point spread function (PSF)

![image-20201230215959789](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201230215959789.png)

ideally point map to point, but that does not exist.

• Superposition (叠加) Principle:

An image is a sum of the PFS of all it's points.

#### Shannon's Sampling Theorem

Sampling must be performed above twice the highest (spatial) frequency of the signal to be lossless.

Given a signal (e.g. an image) with a maximum frequency of $f_{max}$ present, the signal can be reconstructed without loss when sampled above twice  $f_{max}$



### Week 2

(gaussian filter kernal,)

#### Image Transforms

Image Transform = derivation of a new representation of the input data

#### Convolution

Convolution = A mathematical operation on two functions (f and g) that produces a third function (h = f*g), representing how the shape of one is modified by the other.

​											$f * g = \int_{-\infty}^\infty f(x-t)g(x)\partial t$

Convolution in the frequency domain can be implemented by applying the reverse Fourier Transform to both the Fourier Transforms of an image and a kernel, then multiplying the two responses element by element, before applying the forward Fourier Transform to the result.

Convolution can be implemented by applying the forward Fourier Transform to both an image and a kernel, then multiplying the two responses element by element, before applying the reverse Fourier Transform to the result.

The Convolution Theorem states that multiplication in the spatial domain is equivalent to convolution in the frequency domain and vice versa.

#### 2D Discrete Convolution

​								$g(x,y) = \sum_m\sum_n f(x-m,y-n)h(m,n)$

![image-20210102174929499](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210102174929499.png)

#### Median Filter : Noise removal

#### Fourier's Theorem

$f(x) = \int a_n cos(nx) + b_n sin(nx) \delta n$

where $a_n$ and $b_n$ are the Fourier Coefficients.

#### 2D Fourier's Theorem

##### Continuous Form

$F(u,v) = \int_{-\infty}^\infty \int_{-\infty}^\infty f(x,y) e^{-i2\pi(ux + vy)}dxdy$ 

Conversely we can obtain f(x,y) by $f(x,y) = \int_{-\infty}^\infty \int_{-\infty}^\infty F(u,v) e^{-i2\pi(ux + vy)}dudv$ 

##### Discrete Form

$F(u,v) = \frac{1}{N^2}\sum_{x = 0}^{N-1}\sum_{y = 0}^{N-1}f(x,y)e^{i2\pi(\frac{ux + vy}{N})}$

Conversely we can obtain f(x,y) by $f(x,y) = \sum_{u = 0}^{N-1}\sum_{v = 0}^{N-1}F(u,v)e^{i2\pi(\frac{ux + vy}{N})}$

##### Euler's Formula

$e^{i2\pi\frac{ux + vy}{N}} \longrightarrow e^{i\theta} \cos\theta + i\sin\theta$



**Ergo**

$F(u,v) = \frac{1}{N^2}\sum_{x = 0}^{N-1}\sum_{y = 0}^{N-1}f(x,y)[\cos(\frac{2\pi(ux + vy)}{N}) - i\sin(\frac{2\pi(ux + vy)}{N})]$

![image-20210102182150079](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210102182150079.png)

![image-20210102182239783](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210102182239783.png)

#### Conjugate Symmetry

The fourier's transform of a real function f(x,y) give:

$F(u,v) = F*(-u,-v)$									$|F(u,v)| = |F*(-u,-v)|$

Convolution in spatial domain is equivalent to multiplication in frequency domain (and vice versa)

$h = f * g$					implies  			$H = FG$

### Frequency representation

####  Sinusoid Waves

this is power spectrum

![image-20210102213059763](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210102213059763.png)

#### Rotation & Translation

Spatial shifts result in a linear phase change in the frequency domain, but no change in the magnitude spectrum

but rotation will change

![image-20210102212830538](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210102212830538.png)

#### Scaling

Expansion in the spatial domain gives rise to contraction in the frequency domain and vice versa.

 **inverse scaling relationship**

![image-20210102212622588](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210102212622588.png)larger discs translate to smaller central discs in the Fourier spectrum and vice versa

#### line and orientation

Ideal edge and line structures have a concentration of energy along a line passing through the origin in the frequency domain and in a **direction perpendicular to their orientation** - they are ’constructed’ by adding together all 2D sinusoidal waves that ’travel’ perpendicular to the edge or line. 

![image-20210102213258024](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210102213258024.png)

![image-20210102213319435](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210102213319435.png)

#### Contrast

In general the magnitude spectrum determines the contrast and dynamic range of colours in an image whilst the phase determines the structure.

randomise the magnitude will lose the colours

randomise the phase will lose the structure 



a frequency representation gives us a different view of the information present in an image, which can be useful for many tasks, such as filtering. We can easily suppress or enhance certain frequencies, as in low, high or band-pass filtering, or isolate particular image structures with characteristics frequency patterns.

![image-20210117231512392](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210117231512392.png)



### Week 3

![image-20210117214715131](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210117214715131.png)

![image-20210120230730059](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210120230730059.png)

(sobel operaor, image gradient, hough transform algo)

#### Line representation

straight line in 2D space described by a point($p_0,\theta_0$) :

$f(x,y,p_0,\theta_0) = x\cos\theta_0 + y\sin\theta_0-p_0 = 0$

where $p_0$ is the distance between the straight line and the origin and $\theta_0$ is the angle between the distance vector and the positive x-direction

#### Segmentation

1. Thresholding

   set up high and low threshold

2. Split & Merge 

   calculate homogeneous in a certain square

3. Edge-based

4. Region-based

k  means cluster also a way

#### Week 4

#### Haar-like Features

a sub-class of contrast-encoding box features defined by weighted sums/differences over a the average pixel value of a set of adjacent rectangular image regions. They encode fundamental contrast alignments such as edges, lines and point features.

$II(x_1 - 1,y_1 - 1) + II(x_2,y_2) - II(x_2,y_1 - 1) - II(x_1 - 1,y_2)$



#### Integral image

The Integral image II is defined as the double integral of the 2D input image I. It can be calculated by integration along each of the spatial dimensions, thus, it can be defined simply as a discrete sum of sums:

$II(x,y) = \sum^y_0\sum^x_0I(x,y)$

![image-20210102234031616](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210102234031616.png)

is the sum of that square end by that coordinate

$II(-1,y) = 0$		integral image in previous X location				$II(x,y) = II(x-1,y) + A(x,y)$

$A(x,-1) = 0$		 sum over pixels over Y location						$A(x,y) = A(x,y-1) + I(x,y)$

#### Adaboost algorithm

Adaboost is an example of a supervised machine learning algorithm.

Adaboost associates a weight to every positive and negative sample in order to keep track of the algorithm’s per-sample-performance during learning.

Adaboost produces a strong classifier that is a linear combination of weak classifiers, which have to be provided as an input to the learning procedure.

Adaboost normalises its set of weights during every round of the training loop

Initialize weights

normalize the weights

for each feature train a classifier

choose lowest error classifier

update weight

![image-20210117212535632](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210117212535632.png)

#### Week 5

#### Motion Modelling

consider a 3D point $P = (X,Y,Z)$

projects to 2D point: $p = (x,y,f)$	f as focal

![image-20210103214944887](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210103214944887.png)

##### 3D rigid (object do not change shape overtime)motion

R as rotation and T as translation

![image-20210103215320656](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210103215320656.png)

##### Rotation matrix

rotation matrix representing a general 3-D rotation can be written as a product of the individual axis rotation matrices. 	$R = R_X R_Y R_Z$

![image-20210103220232495](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210103220232495.png)

##### 3D motion field

![image-20210103220619889](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210103220619889.png)

##### 2D motion field equation

for image point $p = (x,y,f)$			motion field $v = (v_x, v_y)$

previously mentioned $x = \frac{fX}{Z}$	

$v_x = \frac{dx}{dt} = \frac{d}{dt}(\frac{fX}{Z}) = f\frac{V_XZ - XV_Z}{Z^2}$			(dont understand)

then by above $V_X , V_Y , V_Z$

![image-20210103223110329](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210103223110329.png)



#### Motion estimation

（for rotation only motion, the depth of points in the scene has no impact on the form of the projected motion field）

optical flow and motion are separate

zero optical (apparent motion): polar bear walking in snow

zero motion: light source moving in stationary scene

![image-20210103183202642](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210103183202642.png)

For continuous video $I(x,y,t)$

$I(x + \Delta x, y + \Delta y,t + \Delta t) = I(x,y,t)$

by Taylor series LHS would become $I(x,y,t) + \frac{\delta I}{\delta x}\Delta x + \frac{\delta I}{\delta y}\Delta y+ \frac{\delta I}{\delta t}\Delta t$

#### Optical flow equation

The optical flow equation is based upon the assumption that the intensity of a point along its trajectory( 轨道) in x, y, t space is constant and thus that the rate of change of intensity with time along the trajectory is zero

Optical flow is the changing of pixel colour or intensity between image frames in a sequence due to motion in the scene and/or motion of the camera.

 $\frac{\delta I}{\delta x}\Delta x + \frac{\delta I}{\delta y}\Delta y+ \frac{\delta I}{\delta t}\Delta t = 0$

Dividing throughout by $\Delta t$

$\frac{\delta I}{\delta x} \frac{\Delta x}{\Delta t} + \frac{\delta I}{\delta y} \frac{\Delta y}{\Delta t}+ \frac{\delta I}{\delta t} = 0$

For $\Delta x, \Delta y, \Delta t \to 0$

$\frac{\delta I}{\delta x} \frac{d x}{dt} + \frac{\delta I}{\delta y} \frac{d y}{d t}+ \frac{\delta I}{\delta t} = 0$						**Optical Flow Equation (OFE)**

$\frac{d x}{dt}, \frac{d y}{dt}$  are rate of change of x,y with time 	optical flow field $u = (u_x,u_y)$

$\frac{\delta I}{\delta x}, \frac{\delta I}{\delta y}, \frac{\delta I}{\delta t}$ are rate of change of I with x,y,t	spatial & temporal gradients  $(I_x, I_y, I_t)$

(Ix, Iy and It are the intensity gradients wrt x, y and t, respectively, and vx and vy are the x and y components of the optical flow.)

(Ix, Iy and It are the derivatives of the image intensity along the x, y and t (time) directions at a point and vx, vy are the velocity (motion) of the point along the x and y directions.)

from above we could rearrange it to 	$I_xu_x + I_yu_y +I_t  =0$

[definition for $\nabla$](https://www.khanacademy.org/math/multivariable-calculus/multivariable-derivatives/gradient-and-directional-derivatives/v/gradient)

further rearrange we get $\nabla I.u + I_t = 0^*$	where  $\nabla I.u = I_xu_x + I_yu_y$

**normal flow $u_n$** 	that part of the optical flow vector which is in the same direction as the spatial gradient vector $\nabla I$

$u = u_n + u_p$	where $u_p$ is perpendicular to $u_n$

since perpendicular so $u_p.u_n = 0$ and $\nabla I.u_p = 0$

now back to equation $\nabla I.u + I_t = \nabla I.u_n + I_t = 0$

since we know the direction of $u_n$ we able to get magnitude of $u_n$

$\left \| u_n \right \| = \frac{-I_t}{\nabla I}$				$\angle u_n = \angle \nabla I$	

#### Constant Velocity Model  			(bit lost)

(As we can't get OFE from one since one equation in two unknowns so we make assumptions by considering neighboring  $points == region$ flow vectors are the same. Means we constrain optical flow field to be constant within small regions)

(if its 3D then we need to take x and y in to account)

find the velocity $u = (u_x,u_y)$ which minimises:

$\mathcal{E}(u_x,u_y) = \sum_{region} (I_xu_x + I_yu_y +I_t)^2$

how it achieves the minimisation?

Finding the vx and vy which minimises this equation is achieved by differentiation wrt vx and vy and setting both equations to zero. This results in two linear equations in vx and vy which can be solved.

#### Lucas and Kanade Algorithm

L & K assume theres only one motion in the region

It minimises the deviation from the optical flow equation within the region

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210104234811023.png)

Lucas and Kanade algorithm will not give good estimates of the motion field when the region R is textureless OR contains a single edge OR the region R is on the boundary between two different motions.

![image-20210118220920301](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210118220920301.png)



#### Spatial & Temporal Gradients  

$I_x = \frac{\delta I}{\delta x} \approx I(x+1,y,t) - I(x,y,t)$					assume $\delta x = 1$

#### Affine Motion Model

$u_x = ax + by + c$												$u = Ap$

$u_y = dx + ey + f$												$p^T = (a,b,c,d,e,f)$

In OFE one we rearrange the equation been star

$p^TA^T\nabla I + I_t = 0$			affine OFE (as we did in L&K)	$\hat{p} = M^{-1}b$

$M = \sum_{region} A^T\nabla I \nabla I^T A$									$b = -\sum_{region} I_t(A^T\nabla I)$

(transpose time original will get symmetric matrix, inverse time original is identity)

#### Horn-Schunk Algorithm

(how it achieves the minimisation? differentiation wrt vx and vy and setting both equations to zero)

similar to the L&K,  also aims to minimize the rate of change of the flow field

![image-20210105002117953](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210105002117953.png)



### Week 6

#### Planar Motion

for 3D plane: ( simplified by ignoring the second order terms)

$v_x = a_1x^2 + a_2xy + a_3x + a_4y + a_5 \approx a_3x + a_4y + a_5$

$v_y = a_1xy + a_2y^2 + a_6x + a_7y + a_8 \approx a_6x + a_7y + a_8$		affine motion

#### Simple Two-view Stereo

![image-20210106180503826](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210106180503826.png)

$\frac{T}{Z} = \frac{T-x_L + x_R}{Z-f}$	which rearrange to 	$Z = \frac{fT}{x_L - x_R} = \frac{fT}{d}$	d as disparity(视差)

#### Epipolar (对极)



![image-20210106183213184](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210106183213184.png)

$P_R = R(P_L - T)$	

where $R $ is the rotation matrix 	e.g. clockwise about y-axis $R = \frac{1}{2}\begin{bmatrix}\cos\theta & 0 & \sin\theta \\ 0 & 1 & 0\\ -\sin\theta & 0 & \cos\theta \end{bmatrix}$

Perspective projection (透视投影）:

 $P_L = \begin{bmatrix} X_L \\Y_L \\ Z_L	\end{bmatrix}$					 $p_L = \begin{bmatrix} x_L \\y_L \\ f	\end{bmatrix} = \frac{fP_L}{Z_L}$			 	$p_R = \begin{bmatrix} x_R \\y_R \\ f	\end{bmatrix} = \frac{fP_R}{Z_R}$	





![image-20210106182418812](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210106182418812.png)

Vectors $P_L, T, P_R$ all lie in epipolar plane

$(P_L - T)^T(T\times P_L) = 0$						$\times$ : [cross product](https://www.youtube.com/watch?v=gPnWm-IXoAY)

because dot product is zero for perpendicular vectors

![image-20210106185109619](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210106185109619.png)

this constrains the form that $P_L, P_R$ can take when they form an epipolar plane along with T. As we vary the depth of $P_L$ the $P_R$ also vary.

To simplify the matrix we create **essential matrix** $E$, the geometry of the system 

$E = RS$ 			$P_R^T RS P_L \longrightarrow P_R^T E P_L  = 0$				

![image-20210106192407426](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210106192407426.png)



Let $u_L = EP_L = \begin{bmatrix}u_{L1}\\u_{L2}\\u_{L3}\end{bmatrix}$		

$p^T_REp_L = p^T_Ru_L = x_Ru_{L1 }+ y_Ru_{L2} +fu_{L3}   = 0$	where this is equation of epipolar line in right image system

#### Image points and Pixels

![image-20210106201226605](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210106201226605.png)

$x = s_x(\hat{x} - \hat{O_x})$			$\longrightarrow$				$p_L = \begin{bmatrix}x_L\\ y_L\\f \end{bmatrix} = M_L\begin{bmatrix}\hat{x_L}\\ \hat{y_L}\\f \end{bmatrix} = M_L\hat{p_L}$	$M$ is intrinsic matrix(固有矩阵) which is from above picture $sx,sy,\hat{o_x},\hat{o_y} $

intrinsic matrix including the focal length, image centre and pixel size.

$y = s_y(\hat{y} - \hat{O_x})$					 	$\hat{x_L}, \hat{y_L}$ defines the same points in image plane, but it's in pixel coordinates.

$M = \begin{bmatrix}	s_x & 0 & \frac{-s_x\hat{o}_x}{f}\\	0 & s_y & \frac{-s_y\hat{o}_y}{f}\\ 0 & 0 & 1\end{bmatrix}$

$p^T_REp_L = 0 \longrightarrow \hat{p}^T_R M_R^T E M_L \hat{p}_L = 0$

since $E, M$	are all 3 by 3 matrix, we could make **fundamental matrix**$F = M_R^T E M_L$

thus $ \hat{p}^T_R F \hat{p}_L = 0 $

#### 3D reconstruction

![image-20210106211235432](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210106211235432.png)

$P_R$  $ = R(P_L - T)\\=RP_L - RT$

$P_L$ $ = \frac{P_R + RT}{R}\\=R^TP_R + T$							$R^T = R^{-1}$

now it become

![image-20210106214000936](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210106214000936.png)

$H \begin{bmatrix} a\\b\\c \end{bmatrix} = T$			column of $H$ are from vectors right after constant

so we have $\begin{bmatrix} a\\b\\c \end{bmatrix} = H^{-1}T$			($H$ may not invertible so don't have inverse )

finally the thing we after is by following

![image-20210106214457472](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210106214457472.png)

### Correspondence Matching

#### Region-Based Methods

• Compare pixel values within regions in two views. 

• For region in left image, compute similarity with regions of same size in right image.

 • Corresponding point - centre of most similar region

#### Region Matching

Poor estimates of the projections can result if there are large perspective effects between the two images due to an object being closer to one camera, e.g. OR in areas of repetitive image structure, resulting in mis-matches OR in textureless areas OR if the region straddles a depth boundary (the matching assume a single disparity/depth).

![image-20210106224307549](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210106224307549.png)

#### Similarity Measures

sum of squared differences: $s(u,v) = (u-v)^2$

similar pixel count: $s(u,v) = \begin{cases} 1 & \text{if}|u-v| < T\\0 & \text{otherwise} \end{cases}$

Normalised cross correlation:

$s(u,v) = \frac{(u-\overline{u})(v-\overline{v})}{N_uN_v}$

mean	$u = \frac{1}{|W|}\sum_{u\in W}$					$N_u = \sqrt{\sum_{u\in w}(u-\overline{u})^2}$		Std deviation

#### Feature-Based Methods

• Restrict search to sparse set of features

• Find salient (distinct) points in each view and match points by : 

​	– comparing pixels or image descriptors in local regions about each point

• Example : SIFT matching

#### SIFT Matching

• Two main elements : 

​	 – scale invariant detection of salient (key) points

​	 – matching by highly distinct local descriptors

 • Key point detection : 

​	– extrema (max or min) in difference of Gaussian blurred versions of image 	→ Difference-of-Gaussians (DoG) tree 

​	– points imaged at different resolutions appear at different levels of DoG tree 	→ scale invariance 

• Spatial gradient descriptors: 

​	– built from histograms of spatial gradients in local neighbourhood 

​	– invariant to rotation and perspective warp (almost)

The SIFT descriptor provides a measure of the variation in spatial gradient angle within a region

#### Calibrated

• For calibrated stereo set up, corresponding points lie on epipolar lines 

• Hence, given point in left image, search for point in right image along band about epipolar line: 

• Increases speed, reduces mismatches

![image-20210108164729193](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210108164729193.png)

#### Uncalibrated

• When geometry unknown, can only match points using pixel values – region or feature based approach. 

• Often leads to mismatches amongst true matches, known as outliers and inliers. 

• We know that inliers will be related by epipolar constraint equation $\hat{p}^T_RF\hat{p}_L = 0$

• We can use RANdom SAmple Consensus to sort out: 

​	– select subset of matches at random (minimum 7) 

​	– compute fundamental matrix F from subset (lecture 8, slide 7) 

​	– assess support for F amongst other correspondences 

​	– repeat until best F found