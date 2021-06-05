# interviewbit-databases-sql
Actors and their Movies

https://www.interviewbit.com/problems/actors-and-their-movies/
Write a SQL Query to find the name of those movies where one or more actors acted in two or more movies.

Output Schema:

movie_title
NOTE:

Output column name has to match the given output schema.
Any name is the concatenation(without any delimiter) of first and last name if present
(E.g. if director_first_name is ‘Alfred’ and director_last_name is ‘Hitchcock’ then director_name is ‘AlfredHitchcock’)
Example Output:

movie_title
Vertigo
Schema Design:

Schema Description
![image](https://user-images.githubusercontent.com/4672122/120894111-6b8e0280-c634-11eb-8e8b-2674c7248e31.png)

Solution
select m.movie_title
from movies m join movies_cast mc
on m.movie_id=mc.movie_id join actors a
on mc.actor_id=a.actor_id
and a.actor_id in (select actor_id from movies_cast  
                group by actor_id 
                 having count(*)>=2
                )
