import sys
import matplotlib
matplotlib.use('Agg')

import pandas as pd
import matplotlib.pyplot as plt

# Load your new data
new_data = pd.read_csv("new_data.csv", header=0, sep=",")

# Plotting the line graph with the new data
new_data.plot(x='New_X_Column', y='New_Y_Column', kind='line')
plt.ylim(ymin=0)
plt.xlim(xmin=0)

# Saving the plot to a buffer
buffer = sys.stdout.buffer
plt.savefig(buffer, format='png')
plt.close()  # Close the plot to avoid displaying it

# Writing the buffer content to stdout
buffer.seek(0)
sys.stdout.buffer.write(buffer.getvalue())
sys.stdout.flush()
