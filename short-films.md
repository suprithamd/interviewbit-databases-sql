# interviewbit-databases-sql
https://www.interviewbit.com/problems/short-films/
Write a SQL Query to find those lowest duration movies along with the year, director’s name(first and last name combined), actor’s name(first and last name combined) and his/her role in that production.

Output Schema:

movie_title,movie_year,director_name,actor_name,role
NOTE:

Output column name has to match the given output schema.
Any name is the concatenation(without any delimiter) of first and last name if present
(E.g. if director_first_name is ‘Alfred’ and director_last_name is ‘Hitchcock’ then director_name is ‘AlfredHitchcock’)
Example Output:

movie_title,movie_year,director_name,actor_name,role
Vertigo,1958,AlfredHitchcock,JamesStewart,JohnFerguson
Schema Design:
![image](https://user-images.githubusercontent.com/4672122/120895019-c88bb780-c638-11eb-9615-5749cf191b7b.png)

Solution:
select m.movie_title as movie_title,m.movie_year as movie_year,
concat(d.director_first_name,d.director_last_name) as director_name,
concat(a.actor_first_name,a.actor_last_name) as actor_name, mc.role as role
from movies m join movies_cast mc
on m.movie_id=mc.movie_id join actors a
on a.actor_id=mc.actor_id join movies_directors md
on m.movie_id=md.movie_id join directors d
on md.director_id=d.director_id
group by m.movie_time
having m.movie_time = min(m.movie_time)
