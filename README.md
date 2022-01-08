# Matplotlib_Filling_Area_on_Line_Plots

import pandas as pd
from matplotlib import pyplot as plt

data = pd.read_csv('dt.csv')


ages = data['Age']
dev_salaries = data['All_Devs']
py_salaries = data['Python']
js_salaries = data['JavaScript']
overall_median = 57287

plt.plot(ages,dev_salaries,color = '#444444',linestyle='--',label = 'All Devs')

plt.fill_between(ages,py_salaries,dev_salaries,alpha=0.25,where=(py_salaries>dev_salaries),interpolate=True,label='Above Avg')

plt.fill_between(ages,py_salaries,dev_salaries,alpha=0.25,color='red',where=(py_salaries<=dev_salaries),interpolate=True,label='Below Avg')


plt.legend()
plt.title('Median Salary by Age')
plt.xlabel('Ages')
plt.ylabel('Median Salary (USD)')
plt.tight_layout()
plt.show()
