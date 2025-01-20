# Robot Kinematics: Transformation Matrices Calculation

This notebook involves calculating the transformation matrices for a robotic arm using Denavit-Hartenberg (DH) parameters. The code takes input from you for the DH parameters of each joint and calculates the individual transformation matrices, as well as the final transformation matrix that represents the overall transformation from the base to the end effector.

## Description

In robotics, Denavit-Hartenberg parameters are used to describe the position and orientation of a robot's links and joints. The transformation matrix for each joint is calculated using the following DH parameters:

- **Theta (θ)**: The joint angle around the z-axis.
- **d**: The offset along the z-axis.
- **a**: The length of the common normal (distance between the z-axes of two consecutive joints).
- **Alpha (α)**: The angle between the z-axes of two consecutive joints.

The code allows you to input these parameters for each joint and computes the transformation matrices step-by-step. After calculating the transformation matrices for each joint, the final transformation matrix from the base to the end effector is displayed.

## Requirements

- Python 3.x
- NumPy
- Pandas

You can install the required libraries using pip:

```
pip install numpy pandas
```

## How to Run

1. Run the code in a Python environment.
2. Enter the number of joints in the robotic arm.
3. For each joint, enter the values for the following DH parameters:
    - Theta (θ)
    - d
    - a
    - Alpha (α)
4. The code will display the individual transformation matrices for each joint and the final transformation matrix.

### Example

Let’s consider that, You are working with a 3-joint robotic arm. You will be prompted to enter the values for the DH parameters for each joint, as shown below:

**Input:**
```
Enter the no of joint's: 3

Enter the theta value joint1: 0
Enter the d value joint1: 50
Enter the a value joint1: 0
Enter the alpha value joint1: 90

Enter the theta value joint2: 0
Enter the d value joint2: 0
Enter the a value joint2: 100
Enter the alpha value joint2: 0

Enter the theta value joint3: 0
Enter the d value joint3: 0
Enter the a value joint3: 100
Enter the alpha value joint3: 0
```

**Output:**
```
Transformation Matrix for Joint 1:
 [[ 1. -0.  0.  0.]
 [ 0.  0. -1.  0.]
 [ 0.  1.  0. 50.]
 [ 0.  0.  0.  1.]]

Transformation Matrix for Joint 2:
 [[  1.  -0.   0. 100.]
 [  0.   1.  -0.   0.]
 [  0.   0.   1.   0.]
 [  0.   0.   0.   1.]]

Transformation Matrix for Joint 3:
 [[  1.  -0.   0. 100.]
 [  0.   1.  -0.   0.]
 [  0.   0.   1.   0.]
 [  0.   0.   0.   1.]]

Final Transformation Matrix:
[[  1.   0.   0. 200.]
 [  0.   0.  -1.   0.]
 [  0.   1.   0.  50.]
 [  0.   0.   0.   1.]]
```

The final transformation matrix gives you the complete transformation from the base to the end effector in terms of position and orientation.

## Explanation of Code

1. **Input for DH Parameters:**
   The code asks for the number of joints and the DH parameters for each joint, which you input as floating-point numbers.

2. **Calculation of Transformation Matrices:**
   For each joint, the transformation matrix is calculated using the following formula:


  $$
T_i = \begin{bmatrix}
\cos(\theta_i) & -\sin(\theta_i)\cos(\alpha_i) & \sin(\theta_i)\sin(\alpha_i) & a_i\cos(\theta_i) \\
\sin(\theta_i) & \cos(\theta_i)\cos(\alpha_i) & -\cos(\theta_i)\sin(\alpha_i) & a_i\sin(\theta_i) \\
0 & \sin(\alpha_i) & \cos(\alpha_i) & d_i \\
0 & 0 & 0 & 1
\end{bmatrix}
$$


   This matrix represents the transformation from the previous joint to the current joint.

3. **Final Transformation Matrix:**
   The script multiplies all the individual transformation matrices together to compute the final transformation matrix, which gives the overall transformation from the base to the end effector.

## Contributions

Feel free to contribute by opening issues or submitting pull requests for improvements or new features!
