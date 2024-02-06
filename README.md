Example:

make
dbcreate testdb

minirel testdb

create table soaps(soapid int, name char(28), network char(4), rating real);
load table soaps from ("../data/soaps.data");
print table soaps;
help table soaps; // show attributes of the named relation 

create table stars(starid int, real_name char(20), plays char(12), soapid int);
load table stars from ("../data/stars.data");

/*
 * insert with attributes in order:
 * Dallas, on CBS
 */

insert into soaps (soapid,name,network,rating) values (100, "Dallas", "CBS", 8.67);

/* print names of stars and the soaps they star in */
select stars.plays, soaps.name from stars, soaps where stars.soapid = soaps.soapid;

/* another query */
select soaps.name, stars.starid from stars, soaps  where soaps.name = stars.real_name;

destroy table soaps;
destroy table stars;
help; // show all relations
quit;

dbdestroy testdb

More examples of how to use minirel are found in the testqueries directory
