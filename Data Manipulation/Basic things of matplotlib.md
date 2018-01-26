#Basic things of matplot lib
---

pyplot, or plt, is the central object of ploting.

---
*	Quick plotting
	
	```python

	plt.xlabel('')
	plt.ylabel('')
	plt.title('')
	plt.plot(x,y,'g+--')	#	green, + shape marker, -- line style

	plt.plot(x,y,linestyle='')	# empty linestyle, ie. keep markers only.

	#	plotting multiple series-->call plot multiple times

	```
*	Labels and legends
	
	```python
	plt.plot(x,y, label='series name')

	plt.legend('upper right',fontsize='large') # or plt.legend('best')


	```
* 	histogram
	
	```python

	plt.hist(data_points)
	plt.hist(data_points, bins=3 or [60,70,90,100], rwidth=0.5 or 1 or 1.5)

	plt.hist([data1,data2],color=['green','orange'],label=['series 1', 'series 2'])	# plotting multiple series in one graph

	plt.savefig(bbox_inches='tight',padinches=3,'filename.png',transparent=True)	#	fit the image size with canvas size, give some white space at outer rim, filename, leave the image background transparent.

	```