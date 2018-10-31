What should be the output of the following Script?
v &lt;- c( 2,5.5,6)
t &lt;- c(8, 3, 4)
print(v%/%t)

solution- [1] 0 1 1

2. You have 25 excel files with names as xx_1.xlsx, xx_2.xlsx,........xx_25.xlsx in a dir.
Write a program to extract the contents of each excel sheet and make it one df.

Ans. First of all isntall xlsx package.
install.packages(&quot;xlsx&quot;)
library(&quot;xlsx&quot;)
Then run this command-
library(readxl)
library(dplyr)
library(data.table)
setwd(&quot;E:/Acadgild/Class 1/Assignments&quot;)
file.list &lt;- list.files(pattern=&#39;*.xlsx&#39;) # read the files in directory
# data frame by column with column id
df.list &lt;- lapply(file.list, read_excel)
df1 &lt;- rbindlist(df.list, idcol = &quot;id&quot;)
View(df1)
# data frame by column and if we want file name as column id
df.list &lt;- sapply(file.list, read_excel, simplify = FALSE)
df2 &lt;- rbindlist(df.list, idcol = &quot;id&quot;)
View(df2)

# data frame by row with file names
df3 &lt;- rbind.data.frame(df.list , idcol=&quot;id&quot;)
View(df3)

3. If the above 25 files were csv files, what would be your script to read?

Ans. setwd(&quot;E:/Acadgild/Class 1/Assignments&quot;)

file.list &lt;- list.files(pattern=&#39;*.csv&#39;) # read the files in directory

# data frame by column with column id
df.list &lt;- lapply(file.list, read.csv)
df_csv &lt;- rbindlist(df.list, idcol = &quot;id&quot;)
View(df_csv)

# data frame by column with coulmn id as file name
df.list&lt;- sapply(file.list, read.csv, simplify = FALSE)
df_csv2 &lt;- rbindlist(df.list, idcol = &quot;id&quot;)
View(df_csv2)

# data frame by row with file names in column
df_csv3 &lt;- rbind.data.frame(df.list, idcol = &quot;id&quot;)
View(df_csv3)
