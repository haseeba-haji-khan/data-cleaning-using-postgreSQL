--selecting all
select
*
from
nashville_housing_data.housing_data

--checking soldasvacant column there is some inconsistent data there is Y for Yes and N for No .
select distinct soldasvacant
from
nashville_housing_data.housing_data
----replacing y with yes in solasvacant column and replacing N with No in solasvacant column
update
nashville_housing_data.housing_data
set soldasvacant = 
case when soldasvacant = 'Y' 
THEN 'Yes'
 when soldasvacant = 'N' 
 THEN 'No'
 else soldasvacant
 END
 ------checking updates
select
distinct soldasvacant
from
nashville_housing_data.housing_data
----
select distinct landuse
from
nashville_housing_data.housing_data
--replacing 'VACANT RESIENTIAL LAND' with 'VACANT RESIDENTIAL LAND' in solasvacant column
update
nashville_housing_data.housing_data
set landuse =
case
when landuse = 'VACANT RESIENTIAL LAND'
then 'VACANT RESIDENTIAL LAND'
else landuse
END
----checking updates for landuse
select distinct
landuse
from
nashville_housing_data.housing_data

------checking column propertyaddress is null

select *
from
nashville_housing_data.housing_data
where
propertyaddress is null
order by parcelid
---each paqrcelid has only one propertyaddress but there more than one unit could have same  address if they have same parcelid.using selfjoin tp populate them
select
a.parcelid, b.parcelid,
a.propertyaddress, b.propertyaddress 
from
nashville_housing_data.housing_data as a
join
nashville_housing_data.housing_data as b 
on a.parcelid = b.parcelid
and a.uniqueid <> b.uniqueid
where a.propertyaddress is null
order by a.parcelid
---updating column propertyaddress
update nashville_housing_data.housing_data as a
set propertyaddress = b.propertyaddress
from
nashville_housing_data.housing_data as b 
where a.parcelid = b.parcelid
and a.uniqueid <> b.uniqueid
and a.propertyaddress is null
---checking updates

select *
from
nashville_housing_data.housing_data
where
propertyaddress is null
order by parcelid
----standarizing date
select
to_date(saledate,'DD Mon YY') AS saledate
from
nashville_housing_data.housing_data
----
------checking updates
select
saledate
from
nashville_housing_data.housing_data
---udating standarized date
update nashville_housing_data.housing_data
set
saledate = to_date(saledate,'DD Mon YY') 
----breaking out propertyaddress into invidual columns (address,city,state)
select
split_part(propertyaddress, ',', 1), 
split_part(propertyaddress, ',', 2)
from
nashville_housing_data.housing_data
---updating propertysplitaddress
alter table
nashville_housing_data.housing_data
add split_propertyaddress nchar(300)
---
update nashville_housing_data.housing_data
set
split_propertyaddress = split_part(propertyaddress, ',', 1)
----updating propertysplitcity
alter table
nashville_housing_data.housing_data
add propertysplitcity nchar(300)
-----
update nashville_housing_data.housing_data
set propertysplitcity = split_part(propertyaddress, ',', 2)
---checking updates
select
*
from
nashville_housing_data.housing_data
----updating owneraddress into ownersplitaddress
alter table
nashville_housing_data.housing_data
add ownersplitaddress nchar(300)
---
update nashville_housing_data.housing_data
set ownersplitaddress = split_part(owneraddress, ',', 1)
----updating owneraddress into ownersplitcity
alter table
nashville_housing_data.housing_data
add ownersplitcity nchar(300)
---
update nashville_housing_data.housing_data
set ownersplitcity = split_part(owneraddress, ',', 2)
----updating owneraddress into ownersplitstate
alter table
nashville_housing_data.housing_data
add ownersplitstate nchar(300)
---
update nashville_housing_data.housing_data
set ownersplitstate = split_part(owneraddress, ',', 3)
------checking updates
select
*
from
nashville_housing_data.housing_data

