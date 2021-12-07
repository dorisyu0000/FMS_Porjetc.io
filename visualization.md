# Data Analysis and Visualization 

**Study One**
This graph show the published paper in major social science journal which used social media as their research tool.

{% include_relative Visualization/accpepted_rate.html %}
```
#Publish year orgnize 
df['Published Month'] = df['Published date'].str[0:3]
df['Published Year'] = '20' + df['Published date'].str[4:6]
d = {'Jan':1, 'Feb':2, 'Mar':3, 'Apr':4,'May':5,'Jun':6,'Jul':7,'Aug':8,'Sep':9, 'Oct':10,'Nov':11,'Dec':12 }
df['Published Month']  = df['Published Month'] .map(d)
df.drop('Published date', axis=1, inplace=True)
#Graph 
publication_year =  pd.DataFrame(df['Published Year'].value_counts().reset_index().values, columns=["Year", "Publication_number"])
publication_year = publication_year.sort_values(["Year"], ascending=True)
fig_year = px.line(publication_year, x='Year',y='Publication_number', title='Number of Published Research Paper By Year')
```
