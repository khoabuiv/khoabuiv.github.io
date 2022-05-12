---
layout: post
---

Hello world!
This is the current date and time, as computed by Python:


<html lang="en">
    <script defer src="https://pyscript.net/alpha/pyscript.js"></script>
    <py-script output="plot">
from datetime import datetime
now = datetime.now()
now.strftime("%m/%d/%Y, %H:%M:%S")
    </py-script>
</html>