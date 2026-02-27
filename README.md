# 📊 Power BI Product Color Analysis Dashboard

## 📌 Project Overview

This project demonstrates how raw Excel data can be transformed into structured insights using Power BI.  

The dataset contains product **Color** and **Model** information. Using Power Query, the data was reshaped through Pivot and Unpivot operations and visualized in a clean, professional dashboard.

---

## 🎯 Project Objective

- Transform flat Excel data into structured format  
- Aggregate product count by color  
- Prepare data for visualization  
- Build a simple and effective analytical dashboard  

---

## 🛠 Tools Used

- Power BI Desktop  
- Power Query  
- Excel  
- DAX  

---

## 🔄 Data Transformation Process

1. Imported Excel file into Power BI  
2. Removed unnecessary columns  
3. Promoted first row as headers  
4. Applied appropriate data types  
5. Used **Pivot Column** to count products by color  
6. Applied **Unpivot Columns** to normalize the data  
7. Built dashboard visuals  

---

## 📜 Power Query M Code

```m
Source = Excel.Workbook(File.Contents("C:\Users\User\Downloads\Product_Colour_Model.xlsx"), null, true),
    #"Color Model_Sheet" = Source{[Item="Color Model",Kind="Sheet"]}[Data],
    #"Changed Type" = Table.TransformColumnTypes(#"Color Model_Sheet",{{"Column1", type text}, {"Column2", type text}, {"Column3", type text}}),
    #"Removed Columns" = Table.RemoveColumns(#"Changed Type",{"Column1"}),
    #"Promoted Headers" = Table.PromoteHeaders(#"Removed Columns", [PromoteAllScalars=true]),
    #"Changed Type1" = Table.TransformColumnTypes(#"Promoted Headers",{{"Color", type text}, {"Model", type text}}),
    #"Pivoted Column" = Table.Pivot(#"Changed Type1", List.Distinct(#"Changed Type1"[Color]), "Color", "Model", List.Count),
    #"Unpivoted Columns" = Table.UnpivotOtherColumns(#"Pivoted Column", {}, "Attribute", "Value")
in
    #"Unpivoted Columns"
_________________________________________________________________________________________________
📊 Dashboard Features
🔢 KPI Card – Total Products
📈 Column Chart – Products by Color
🥧 Pie Chart – Percentage Distribution
Clean and structured layout
_________________________________________________________________________________________________
💡 Key Learnings
Understanding Pivot vs Unpivot
Applying aggregation functions (Count)
Preparing data for reporting
Designing simple business dashboards
_____________________________________________________________________________________________________
👩‍💻 Author
Vidya Vishnuvihar Geetha
Aspiring Data Analyst
