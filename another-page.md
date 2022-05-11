---
layout: post
---

Hello world!
This is the current date and time, as computed by Python:


<html lang="en">
  <body>
    <py-script>
from datetime import datetime
now = datetime.now()
now.strftime("%m/%d/%Y, %H:%M:%S")
    </py-script>
  </body>
</html>