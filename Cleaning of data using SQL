-- //creating a workiing table\\
create table layoffs_work
select * from layoffs;
select * from layoffs_work;

-- //delete dublicate columns\\
-- assign row number to each distinct row
select * , row_number () over(
partition by company, location, industry, total_laid_off,percentage_laid_off, date,stage,country,funds_raised_millions)
as rowno
from layoffs_work;

-- create a table which contains row number 
create table layoffs_work2 (
select * , row_number () over(
partition by company, location, industry, total_laid_off,percentage_laid_off, 'date', stage,country,funds_raised_millions)
as rowno
from layoffs_work);

-- determining the dublicates
select * from layoffs_work2
where rowno >1
order by company;
-- checking for accuracy
select * from layoff_work2
where company = 'casper';

-- deleting the dublicates
delete from layoffs_work2
where rowno>1;

-- // standarization of data//
-- remove empty spaces 
select  company, trim(company) from layoffs_work2;

update layoffs_work2 
set company = trim(company);

select * from layoffs_work2;

select distinct location from layoffs_work2
order by location;

select distinct country from layoffs_work2
order by country;

select  country from layoffs_work2
where country like 'United States%';

update   layoffs_work2 
set country = 'United States'
where country like 'United States%' ;

select country from layoffs_work2 
where country like 'United States.';

select* from layoffs_work2;

select* from layoffs_work2
where total_laid_off is null
and percentage_laid_off is null;

delete from layoffs_work2
where total_laid_off is null
and percentage_laid_off is null;

select * from layoffs_work2
where industry is null or 
industry ='';

select * from layoffs_work2
where company ='Airbnb';

select * from layoffs_work2 t1 
join layoffs_work2 t2 
on t1.company = t2.company
where t1.industry is null
and t2.industry is not null;


update  layoffs_work2
set industry = null
 where industry ='';


update   layoffs_work2 t1 
join layoffs_work2 t2 
on t1.company = t2.company
set t1.industry = t2.industry
where t1.industry is null
and t2.industry is not null;


select * from layoffs_work2;

update layoffs_work2
set `date` = str_to_date(`date`,'%m/%d/%Y');

UPDATE layoffs_work2
SET `date` = STR_TO_DATE(`date`, '%m/%d/%Y');


alter table layoffs_work2
modify date date;


select `date`,STR_TO_DATE(`date`, '%m/%d/%Y') from layoffs_work2;

alter table layoffs_work2
drop column rowno;
