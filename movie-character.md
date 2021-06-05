# interviewbit-databases-sql

Movie Character
https://www.interviewbit.com/problems/movie-character/
Write a SQL Query to find the movie_title and name of director (first and last names combined) who directed a movie that casted a role as ‘SeanMaguire’.

Output Schema:

director_name,movie_title
NOTE:

Output column name has to match the given output schema.
Any name is the concatenation(without any delimiter) of first and last name if present
(E.g. if director_first_name is ‘Alfred’ and director_last_name is ‘Hitchcock’ then director_name is ‘AlfredHitchcock’)
Example Output:

director_name,movie_title
AlfredHitchcock,Vertigo
Schema Design:
![image](https://user-images.githubusercontent.com/4672122/120894295-477ef100-c635-11eb-9b3c-cf24575c4e2e.png)

Solution:
select concat(d.director_first_name ,d.director_last_name) as director_name,m.movie_title as movie_title
from movies m join movies_cast mc
on m.movie_id=mc.movie_id join movies_directors md
on m.movie_id=md.movie_id join directors d
on d.director_id = md.director_id
where role='SeanMaguire'
