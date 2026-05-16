# Defog - Dark Channel Prior

*It is based on a key observation - most local patches in haze-free outdoor images contain some pixels which have very low intensities in at least one color channel.* 

$I(x) = J(x)t(x) + A(1 - t(x))$

I is the observed intensity
J is the scene radiance.
A is the global atmospheric light.
The first term J(x)t(x) on the right-hand side is called direct attenuation , and the second term A(1-t(x)) is called airlight.

t is the medium transmission describing the portion of the light that is **NOT** scattered and reaches the camera. 

The goal of haze removal is to recover J, A, and t from I. 
From the above equation, we got the colinear system in RGB scalar like:

![image.png](Defog%20-%20Dark%20Channel%20Prior/image.png)

$$
I(x) - A = t(x)\,(J(x) - A)
$$

$$
A - I(x) = t(x)\,(A - J(x))
$$

$$
\|A - I(x)\| = t(x)\,\|A - J(x)\|
$$

$$
t(x)= \frac{\|A - I(x)\|}{\|A - J(x)\|}
$$

$$
A_c - I_c(x)= t(x)\,(A_c - J_c(x)) (c \in {r,g,b})
$$

$$
t(x)= \frac{A_c - I_c(x)}{A_c - J_c(x)}
$$

For an N-pixel color image I, there are 3N constraints and 4N+3 unknowns.

> [Single image haze removal using dark channel prior | IEEE Conference Publication | IEEE Xplore](https://ieeexplore.ieee.org/document/5206515)
> 

But what’s x? Is it the distance to object or the 2D location?  Is A the amplitude? what’s the relationship between A and J?

![image.png](Defog%20-%20Dark%20Channel%20Prior/image%201.png)

The optical model of the bad weather derived into two terns:

$$
I(x)=L_{\infty}\rho(x)e^{-\beta d(x)}+L_{\infty}\left(1-e^{-\beta d(x)}\right).
$$

First tern is the direct attenuation, and the second term is the airlight. 

I is the image intensity. 
x is the 2D spatial location. 
$L_{\infty}$ is the atmospheric light, which is commonly assumed to be globally constant; thus, it is independent of location x. 
ρ is the reflectance of an object in the image. 
β is the atmospheric attenuation coefficient. 
d is the distance between an object in the image and the observer.

> [Visibility in bad weather from a single image | IEEE Conference Publication | IEEE Xplore](https://ieeexplore.ieee.org/document/4587643)
> 

Now, we have the conditions:

1. In the nature image, one of every RGB values is closed to zero.
2. We saw the object, the image signal is both composed by direct attenuation and airlight.
3. The materials we have are 
    1. x, position
    2. I, intensity
    3. Assume the object distance d is unlimited,  $e^{-\beta d(x)}$ (t(x))is 0. 
    I(x) = $L_{\infty}$. All signal intensity depends on the enviroment light.
    4. Assume there is no effect of scattering particles ($e^{-\beta d(x)}$ =1)
     I(x) = $L_{\infty}\rho(x)$, All signal intensity are equal to light reflected by object. make sense.

Now, we undertand the limited value, how about the normal value of (t(x),  $e^{-\beta d(x)}$) (1-t(x), 1-$e^{-\beta d(x)}$)?