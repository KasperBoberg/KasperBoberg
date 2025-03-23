![1  Importing_Database_Anon](https://github.com/user-attachments/assets/c89bb1b4-d735-4790-85af-f9a0c24acb88)

First step is creating the database on supabase.com. The database is based on PostgreSQL. 
The data set is stored under public.streaming_data and contains approximately 27000 rows. 

![2  Imported_Database_Anon](https://github.com/user-attachments/assets/c65f30c5-6462-4525-99c4-29af558f30ce)

The supabase interface is used to correctly label and format the columns (TEXT, INT, DATE, etc). The data was also at this step anonymized so that the final Power BI dashboards can be made public.

![4  Debug_DBeaver_Anon](https://github.com/user-attachments/assets/d9464f89-498b-46a4-a533-d7ba9c7cd503)

Via DBeaver, connection with the database was controlled.

![5  Alter_Table_Formatting_Anon](https://github.com/user-attachments/assets/577d3be5-abf2-45a3-96db-ef6f0b5ff27c)

Basic querying was at this stage performed, such as *alter table* to correctly reformat the columns and remove case-sensitivity.
