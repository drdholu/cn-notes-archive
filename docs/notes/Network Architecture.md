How exactly are networks designed in the real world? What are the design criteria's they follow? How are failure points avoided? These answers are all answered by the network architecture we will discuss.

A bad system design consists of a **single point of failure**, where one switch connects another switch which in the end connects to multiple devices. Failure of the first switch, could lead to failure of the devices indirectly connected to it. This can be avoided by simply following some kind of architecture rules.

![Pasted image 20240610205457.png](./images/Pasted%20image%2020240610205457.png)

> This is formally called as **Daisy Chaining of Switches**

# 2 Tier Architecture

As we saw above, failure in one device could lead to failure in other devices too. To prevent this (not completely), we make use of the 2 Tier architecture.

What are the two tiers?
1. Access layer
2. Distribution layer

Here instead of one switch connecting to other, we introduce a **Multi layer switch**. Now unlike normal switches, the multi layer switch works in **L3** layer, i.e. it deals with **IP-addresses**. It's almost similar to routers, but routers can't send out packets like a switch.

Using this new multi layer switch, our smaller connections which include a switch and other devices connected to it (forms the access layer) are connected to the multi layer switch and this connects to the router (the switch and router form the distribution layer).

Now this is significantly better than what we had before, but we **still have a single point of failure**.

![Pasted image 20240610210918.png](./images/Pasted%20image%2020240610210918.png)

# 3 Tier Architecture

Now someone decided to add another complicated layer of single point of failure, Great. This layer is almost similar to 2 tier, but this one contains **3 layers**.

What are the layers?
1. Access Layer
2. Distribution Layer
3. **Core Layer**

The access layer and the distribution layer are still the same, but the distribution layer, or the multi layer switches of the dist. layer are connected to **more multi layer switches**, specifically **2**. These are the **backbones of the architecture**. These new switches are then connected to **two routers**.

This architecture is used by large enterprises as they are quite expensive compared to our previous architectures.

![Pasted image 20240610224451.png](./images/Pasted%20image%2020240610224451.png)

# Collapsed 2 Tier Architecture

Now smaller enterprises wanted something similar to the 3 tier arch. but something more inexpensive. The collapsed 2 tier architecture solves that. I

t's **almost similar to the normal 2 tier architecture** but instead of one multi layer switch in the distribution layer, it contains **two**. This reduces the single point of failure, which is why it's also more ideal than the normal 2 tier architecture.

![Pasted image 20240610224154.png](./images/Pasted%20image%2020240610224154.png)