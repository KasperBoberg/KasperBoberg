![1  Importing_Database](https://github.com/user-attachments/assets/522585f7-2bd5-4f45-b4d7-5602f9217c84)

First step is creating the database on supabase.com. The database is based on PostgreSQL. 
The data set is stored under public.streaming_data and contains approximately 27000 rows. 

![2  Imported_Database](https://github.com/user-attachments/assets/98f24a27-4975-4f6a-93b2-07f07db099a4)

The supabase interface is used to correctly label and format the columns (TEXT, INT, DATE, etc). 

![4  Debug_DBeaver](https://github.com/user-attachments/assets/a9dfe9cf-9a06-4564-99ef-44769af816a9)

Via DBeaver, connection with the database was controlled.

![5  Alter_Table_Formatting](https://github.com/user-attachments/assets/e3bcd9e3-d1e5-44b1-88ae-4dea41dab743)

Basic querying was at this stage performed, such as *alter table* to correctly reformat the columns and remove case-sensitivity.
