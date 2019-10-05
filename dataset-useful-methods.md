---
description: List of Useful Methods
---

# 1.4 Dataset Useful Methods

### Replace Nulls from String Nulls

```java
private static Dataset<Row> replaceNull(Dataset<Row> df, String[] cl) {
		for(String g : cl){
 	df = df.withColumn(g,
			 			functions.when(df.col(g).equalTo("null"), null).otherwise(df.col(g))
						);	
			 
		}
		return df;
		 
	}
	
Dataset<Row> DS_With_NUlls	replaceNull(DS,DS.Columns());
```

### Change Every datatype to String Type

```java
private static Dataset<Row> castToString(Dataset<Row> df,String[] dfcols){
		
		Column[] Casts = Arrays.stream(dfcols).map(f -> df.col(f).cast(DataTypes.StringType)).toArray(Column[]::new);
		return df.select(Casts);
	}

```

### Replace Column name where Spaces and square brackets

```java
private static Dataset<Row> renameColsDS(Dataset<Row> df1, String[] df1cols) {
		Column[] f = Arrays.stream(df1cols).map(f1 -> df1.col(f1).alias(f1.replaceAll(" ","_").replaceAll("[()]",""))).toArray(Column[] :: new);
		 
		return  df1.select(f);
	}

```

