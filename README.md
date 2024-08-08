# RETAIL TRANSACTION PROJECT

# PROBLEM STATEMENT
This is a dataset containing retail transactions from a large retailer, with over 100 thousand records spanning 2 years. Each record represents a single transaction and includes features such as:

Customer ID (Anonymous)
Product ID
Quantity
Price
Transaction Date
Discount Applied
Payment Method
Store Location etc. My goal is to analyze this dataset to determine:
The Total Amount by Day Name
The Total Amount by Month Name
The Total Amount Quarterly
The Total Amount Yearly
The Total Number of Product sold
The Total Amount of Discount Applied for each Payment Method.

# LIBRARY USED
- Matplotlib
- Pandas
- Numpy

# STEPS
- Rounding up the TotalAmount column to a nearest decimal place. Retail_sale["TotalAmount"]=Retail_sale["TotalAmount"].round().
- Converting the TransactionDate column from an object type to datetime type. Retail_sale["TransactionDate"]=pd.to_datetime(Retail_sale["TransactionDate"])

#### TRANSACTION PER DAY
- Retail_sale['Day_Name']=Retail_sale['TransactionDate'].dt.day_name()
- Day=Retail_sale.groupby("Day_Name")["TotalAmount"].sum()
- Day
- Name=Day.index
- Numbers=Day.values
- plt.bar(Name,Numbers,color="green")
- plt.title("TRANSACTION PER DAY",fontsize=16,fontweight="bold",fontstyle="italic")
- plt.xlabel("Name of day")
- plt.ylabel("Number per day")
- plt.savefig("TRANSACTION PER DAY")
- plt.show()
  
![TRANSACTION PER DAY](https://github.com/user-attachments/assets/6380bfb5-1190-4ca2-b7a5-843955e3ca6f)


#### TRANSACTION PER MONTH
- Retail_sale['Month_name']=Retail_sale['TransactionDate'].dt.month_name()
- Month=Retail_sale.groupby("Month_name")["TotalAmount"].sum()
- Month
- Name1=Month.index
- Numbers1=Month.values
- plt.pie(Numbers1,labels=Name1,shadow=True,autopct="%1.0f%%",explode=[0.1,0.1,0,0,0,0.1,0.1,0,0,0.1,0.1,0])
- plt.title("TRANSACTION PER MONTH",fontsize=16,fontweight="bold",fontstyle="oblique")
- plt.savefig("TRANSACTION PER MONTH")
- plt.show()
  
![TRANSACTION PER MONTH](https://github.com/user-attachments/assets/baeb7764-7501-4305-a230-ac204e3ef1a0)

#### TRANSACTION PER QUARTER
- Retail_sale['Quarter']=Retail_sale['TransactionDate'].dt.quarter
- Qtr=Retail_sale.groupby("Quarter")["TotalAmount"].sum()
- Qtr
- Name2=Qtr.index
- Numbers2=Qtr.values
- plt.barh(Name2,Numbers2,color="purple")
- plt.title("TRANSACTION PER QUARTER",fontsize=16,fontweight="bold",fontstyle="italic")
- plt.xlabel("Number per Qtr")
- plt.ylabel("Count per Qtr")
- plt.savefig("TRANSACTION PER QUARTER")
- plt.show()
  
![TRANSACTION PER QUARTER](https://github.com/user-attachments/assets/3d12a0b8-c660-475f-bd87-c3b78ebcb414)

#### TRANSACTION PER YEAR 
- Retail_sale['Year']=Retail_sale['TransactionDate'].dt.year
- Year=Retail_sale.groupby("Year")["TotalAmount"].sum()
- Year
- Name3=Year.index
- Number3=Year.values
- plt.plot(Name3,Number3,color="Black",marker="*")
- plt.title("TRANSACTION PER YEAR",fontsize=14,fontstyle="italic",fontweight="bold")
- plt.xlabel("Number per Year")
- plt.ylabel("Count per Year")
- plt.savefig("TRANSACTION PER YEAR")
- plt.show()
  
![TRANSACTION PER YEAR](https://github.com/user-attachments/assets/d3469e11-771e-4894-9b5c-e0c7c57c74a1)

#### Total Number of Product Sold
- ProductCat=Retail_sale.groupby("ProductCategory")["TotalAmount"].count()
- ProductCat
- Name4=ProductCat.index
- Number4=ProductCat.values
- plt.pie(Number4,labels=Name4,shadow=True,autopct="%1.0f%%",explode=[0.1,0.1,0.1,0])
- plt.title("Total Number of Product Sold",fontsize=14,fontweight="bold",fontstyle="oblique",c="g")
- plt.savefig("Total Number of Product Sold")
- plt.show()
  
![Total Number of Product Sold](https://github.com/user-attachments/assets/8173ce12-71db-4683-9d73-50a046a3416e)

#### DISCOUNT APPLIED FOR EACH PAYMENT METHOD
- Paymet=Retail_sale.groupby("PaymentMethod")["DiscountApplied(%)"].sum()
- Paymet
- plt.plot(Name5,Number5,marker="+")
- plt.title("DISCOUNT APPLIED FOR EACH PAYMENT METHOD",fontsize=14,fontstyle="italic",fontweight="bold",c="b")
- plt.xlabel("Payment Method")
- plt.ylabel("Discount Applied(%)")
- plt.savefig("DISCOUNT APPLIED FOR EACH PAYMENT METHOD.png")
- plt.show()
  
![DISCOUNT APPLIED FOR EACH PAYMENT METHOD](https://github.com/user-attachments/assets/805ad2c9-96cc-438e-ae28-bc69ef575e91)

# SCREENSHOT OF THE CHART IN SUBLOT 
- fig,Retails=plt.subplots(nrows=2,ncols=3,figsize=(14,8))
- fig.suptitle("RETAIL TRANSACTION REPORT", fontsize=40,fontstyle="normal",fontweight="bold",c="r")
- Retails[0,0].bar(Name,Numbers,color="green")
- Retails[0,1].pie(Numbers1,labels=Name1,shadow=True,autopct="%1.0f%%",explode=[0.1,0.1,0,0,0,0.1,0.1,0,0,0.1,0.1,0])
- Retails[0,2].barh(Name2,Numbers2,color="purple")
- Retails[1,0].plot(Name3,Number3,color="Black",marker="*")
- Retails[1,1].pie(Number4,labels=Name4,shadow=True,autopct="%1.0f%%",explode=[0.1,0.1,0.1,0])
- Retails[1,2].plot(Name5,Number5,marker="+")
- Retails[0,0].set(title="TRANSACTION PER DAY")
- Retails[0,1].set(title="TRANSACTION PER MONTH")
- Retails[0,2].set(title="TRANSACTION PER QUARTER")
- Retails[1,0].set(title="TRANSACTION PER YEAR")
- Retails[1,1].set(title="DISCOUNT APPLIED FOR EACH PAYMENT METHOD")
- plt.tight_layout()
- plt.savefig("RETAIL.png")
- plt.show()
  
![RETAIL](https://github.com/user-attachments/assets/313bdae6-d295-4aa5-bf89-a5f08f8e3e23)

