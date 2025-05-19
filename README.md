SELECT * FROM blinkit_da.`blinkit grocery data`;

/* 
select count(*) from blinkit_da.`blinkit grocery data`;
to check how many rows were imported 
*/

/* cleaning item fat content */

update 
	blinkit_da.`blinkit grocery data`
set 
	`Item Fat Content` = case 
when 
	`Item Fat Content` in ('Lf', 'low fat') then 'Low fat'
when
	`Item Fat Content` in ('reg','Regulae') then 'Regular'
else
    `Item Fat Content`
end;

/*
[verifify the item fat content]
select distinct `Item Fat Content` from blinkit_da.`blinkit grocery data`
*/

select `Item Fat Content`, 
	cast(sum(`Total Sales`) as decimal(10,2)) as `Tot sales`,
    cast(avg(`Total Sales`) as decimal(10,2)) as `Avg sales`,
    count(*) as `Tot num`,
    avg(`Rating`) as Avg_rateing
from blinkit_da.`blinkit grocery data`
group by `Item Fat Content`
order by `Tot Sales` desc;


/*
verifying item type feild
select distinct`Item Type` from blinkit_da.`blinkit grocery data`;
*/
select `Item Type`, 
	cast(sum(`Total Sales`) as decimal(10,2)) as `Tot sales`,
    cast(avg(`Total Sales`) as decimal(10,2)) as `Avg sales`,
    count(*) as `Tot num`,
    avg(`Rating`) as Avg_rateing
from blinkit_da.`blinkit grocery data`
group by `Item Type`
order by `Tot Sales` desc;

/*
verifying `Outlet Location Type` feild
select distinct `Outlet Location Type` from blinkit_da.`blinkit grocery data`;
*/
select `Outlet Location Type`, 
	cast(sum(`Total Sales`) as decimal(10,2)) as `Tot sales`,
    cast(avg(`Total Sales`) as decimal(10,2)) as `Avg sales`,
    count(*) as `Tot num`,
    avg(`Rating`) as Avg_rateing
from blinkit_da.`blinkit grocery data`
group by `Outlet Location Type`
order by `Tot Sales` desc;

/*
verifying `Outlet Establishment Year` feild
select distinct `Outlet Establishment Year` from blinkit_da.`blinkit grocery data`;
*/
select `Outlet Establishment Year`, 
	cast(sum(`Total Sales`) as decimal(10,2)) as `Tot sales`,
    cast(avg(`Total Sales`) as decimal(10,2)) as `Avg sales`,
    count(*) as `Tot num`,
    avg(`Rating`) as Avg_rateing
from blinkit_da.`blinkit grocery data`
group by `Outlet Establishment Year`
order by `Outlet Establishment Year`;
