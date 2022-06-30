#Data Cleaning Projects using PostgreSQL
 
A SQL data cleaning project using Nashville housing data.

#The Following Processes I have done in this project

•Changing Y and N to Yes and No in the SoldAsVacant field and landuse field using CASE statement.

•By using a SELF JOIN, populated the PropertyAddress fields where the value is NULL and updated the table.

•Standardized date format using TO_DATE and updated the table.

•Splitting propertyaddress into individual column as propertysplitaddress, propertysplitcity and updated the table using SPLIT_PART .

•Splitting owneraddress into individual column as ownersplitaddress, ownersplitcity, and ownersplitstates updated the table using SPLIT_PART.
