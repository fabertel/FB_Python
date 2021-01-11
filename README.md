# FB_Python

use for public sharing https://nbviewer.jupyter.org/github/fabertel/FB_Python/blob/main/NBA2020analytics.ipynb

https://nbviewer.jupyter.org/github/fabertel/FB_Python/blob/main/NBA2020analytics%20-%20OK.ipynb

JUPYTER LABS EXTENSIONS 

@lckr/jupyterlab_variableinspector
@jupyterlab/github
@jupyter-widgets/jupyterlab-manager
@jupyterlab/google-drive

TO INSTALL 
jupyter labextension install @jupyterlab/google-drive


--------------------------------

# PLACE ORDERS 
# degiro.buyorder(Order.Type.LIMIT,5396380, 3, 3, 147)
# degiro.buyorder(Order.Type.LIMIT,14902751, 3, 7, 57)
degiro.buyorder(Order.Type.LIMIT,4622784, 3, 11, 61)

# EXTRACT ORDERS 
import pandas as pd 
from datetime import datetime, timedelta
orders = degiro.orders(datetime.now() - timedelta(days=4), datetime.now())
orders_log = pd.DataFrame(orders)
orders_log = orders_log.sort_values(["orderId", "last"], ascending = (False, False))
sorted = orders_log.sort_values(by=('last'), ascending=False)
result = sorted.drop_duplicates('orderId', keep='first')
result = result[(result.type=="CREATE")&(result.status=="CONFIRMED")]
result   #isActive=FAlse (processato) , True (still open) 
