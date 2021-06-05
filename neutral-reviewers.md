# interviewbit-databases-sql
https://www.interviewbit.com/problems/neutral-reviewers/
Write a SQL Query to find the name of all reviewers who have rated their ratings with a NULL value.

Output Schema:

reviewer_name
NOTE: Output column name has to match the given output schema.

Example Output:

reviewer_name
MaxPlank
NeilsBohr
Schrodinger
Schema Design:
![image](https://user-images.githubusercontent.com/4672122/120894358-99c01200-c635-11eb-8eee-4684c237ec1f.png)

Solution:
select re.reviewer_name
from ratings ra join reviewers re
on ra.reviewer_id = re.reviewer_id
group by ra.number_of_ratings
having count(ra.reviewer_stars) is NULL
