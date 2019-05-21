#Download tpch tool from the website and unzip it
cd dbgen
cp makefile.suite Makefile

#Update Makefile with
#CC=gcc
#DATABASE=ORACLE
#MACHINE=LINUX
#WORKLOAD=TPCH

make
<PATH-TO-TOOL>/dbgen -s 1

#Check if tables are generated
ls -l *.tbl

#Remove | and convert to csv
for i in `ls *.tbl`; do sed 's/|$//' $i > ${i/tbl/csv}; echo $i; done;


#create a psql database and run file tpch-build.sql (make sure to change path in the sql file accordingly)