---
layout: post
---

Hello world!
This is the current date and time, as computed by Python:


<html lang="en">
    <script defer src="https://pyscript.net/alpha/pyscript.js"></script>
    <py-script>
import matplotlib.pyplot as plt
import numpy as np

x = np.random.randn(1000)
y = np.random.randn(1000)

fig, ax = plt.subplots()
ax.scatter(x, y)
fig
    </py-script>
</html>