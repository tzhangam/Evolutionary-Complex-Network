#Good things in Pandas
---
Dataframe object is the core and soul of Pandas.

---

*	Creation
	
	```python
	df=pd.read_csv("filename.csv")
	df=pd.read_excel("filename.xlsx","sheet1")
	
	w={'name':[1,2,3],'name2':[...]} 	# w is a python dictionary, key is column name, value is column values

	df=pd.Dataframe(w)	# convert a dictionary to Dataframe
	```

*	Data cleaning upon reading
	```python
	df=pd.read_csv("filename.csv",skiprows=1)	
	#skipping the first row

	df=pd.read_csv("filename.csv",header=None,names=['col_name1','col_name2'])	#	Provide column names manually.


	df=pd.read_csv("filename.csv",nrows=20,na_values=['not availible','n.a']) # read first 20 rows only, #Treat 'not availible' and 'n.a' as na_value,i.e. assign them  with NaN value.

	df=pd.read_csv('filename.csv',na_values={
		'column_1':['n.a','not availible'],
		'column_2':[-1]
		})
		#	Passing in a dictionary to individually specify what values in which row should be treated as NaN value.

	df=pd.read_excel("name.xlsx","sheet1",converters={
		"col1": converter_function_name
		})
		#	We can specify a function for each column to use when converting a excel file's cells.
	```
*	Futher data cleaning
	```python
	df.fillna(0,inplace=true)	# Fill NaN values in df with zero
	df.fillna({
		the replacement rule list for each column
		})
	df.fillna(method="ffill",inplace=true) # forward fill method.
	df.fillna(method="bfill",inplace=true,limit=1)	# backward fill, copy only once if multiple NaN consecutively exists


	new_df=df.interpolate() #	Using linear interpolation to deal with missing value.
	new_df=df.interpolate(method="methodname")	# Specify a interpolationg method. e.g. linear interpolate w.r.t time, etc.

	df.dropna(inplace=true)	#drop na rows
	df.dropna(how="all")	#drop row if it is entirely empty
	df.dropna(thresh=2)	# Do not drop row if it has at least 2 valid values.

	dt=pd.date_range("day1","dayend")
	idx=pd.DatetimeIndex(dt)
	new_df=df.reindex(idx)	# Re-index df using our particularly specified indexes, possibly creating new empty rows if necessary.
	```

*	Row column access
	
	df.shape
	df.column 	# all columns of df as a list
	df.index 	# the row index list

	#	Atomic instances that constitutes a dataframe is its rows.

	df.head(2) # The first 2 rows
	df.tail(3)	# The last 3 rows

	df[1:3]	# 1st and 2nd row

	#	Accessing coloumns using column name

	
	df['column name'] # this is actually a Series object

	df[['column_name1','column_name2']]	# multiple columns

*	Functions

	df['column_name'].max() # or mean(), min() etc.

	df.describe()	# statistis basics of number entries of df

	#	Advance querying
	df[df.temperature==df['temperature'].max()]	# Return the ROW that has the maximum temperature
	#	LHS is a placeholder, RHS is an actual call

	df[['columnname']][df.temperature==df['temperature'].max()]

*	Index formatting
	
	```python
	df.index

	df.set_index('column_name_1',inplace=Tre)	# Let the column_name_1 values serves replace the default natural number indexes, inplace.

	df.loc['index_value'] # Access the particular row(s) corresponding to index_value. It acts like a simple hash function

	df.reset_index(inplace=True)	# reset to default indexing	

	```


*	Writing to files
	
	```python
	
	df.to_csv("filename.csv",index=False, header=False)	# Don't print defualt index to file, don't print header either

	df.to_csv("filename.csv",columns=['col1','col2'])	# Only write 2 columns specified to file.

	df.to_excel('filename.xlsx',sheet_name='sheetname',startrow=1, startcol=2)

	with pd.ExcelWriter('filename.xlsx') as writer:
		df_1.to_excel(writer,sheet_name='df_1')
		df_inf.to_excel(writer,sheet_name='df_inf')
	#	Use a pd writer object to write multiple dataframes to different sheets of a same xlsx file.
	```

*	Pivot


*	Concat
	
	df3=pd.concat([df1,df2],ignore_index=True)	#df1 and df2 are of the same header name, appending in rows

	df3=pd.concat([df1,df2], keys=['df1','df2'])	# Giving the subgroups of df3 names as keys

	df3=pd.concat([df1,df2], axis=1)	#	Append df2 to df1 as a new column.

	#	we can manually input index for df1, df2 upon creation, so that the appending alignment is correct w.r.t index. 


* 	Series
	
	a=pd.Series(["value1","value2","value3"],name="col_x")

	df3=pd.concat([df1,a],axis=1)	# Add a new series as a new column to df1.

* 	Merging
	
	 df3=pd.merge([df1,df2], on="column_name")	# Merge df1 and df2, given they have a same column_name, and are of the same number in rows. If not, the intersection of on values are kept.

	 df=pd.merge([df1,df2],on="column_name",how="outer") # THis is the union of values are kept, this is outer join. By default it is inner join. We can also have left join, decided by the order of df1,df2 which join is used.


*	and stacking dataframe, data 


