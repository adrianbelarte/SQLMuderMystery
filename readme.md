---pista 1--

SELECT name 
  FROM sqlite_master
 where type = 'table'

--pista 2--

SELECT sql 
  FROM sqlite_master
 where name = 'crime_scene_report'

--pista 3 --

SELECT * 
FROM crime_scene_report
WHERE date = '20180115' AND city = 'SQL City';

-last house on 'Northwestern Dr'.
-named Annabel, lives somewhere on 'Franklin Ave'.

--pista 4 --

SELECT * 
FROM person
WHERE address_street_name = 'Northwestern Dr'
ORDER BY address_number DESC
LIMIT 1;

id	    name	        license_id	address_number	address_street_name	  ssn
14887	Morty Schapiro	118009	    4919	         Northwestern Dr	  111564949

-- pista 5 --

SELECT * 
FROM person
WHERE name LIKE 'Annabel%' AND address_street_name = 'Franklin Ave';

id	    name	        license_id	address_number	address_street_name	 ssn
16371	Annabel Miller	490173	    103	             Franklin Ave	     318771143

-- pista 6 --

SELECT * 
FROM interview
WHERE person_id = 14887 OR person_id = 16371;

-He had a "Get Fit Now Gym" bag.
- membership number started with "48Z".
-  man got into a car with a plate that included "H42W".
- last week on January the 9th.

-- pista 7 -- 

SELECT *
FROM get_fit_now_member
WHERE id LIKE '48Z%' AND membership_status = 'gold';


id	    person_id	name	        membership_start_date	membership_status
48Z7A	28819	    Joe Germuska	20160305	            gold
48Z55	67318	    Jeremy Bowers	20160101	            gold

-- pista 8 --

SELECT *
FROM get_fit_now_check_in
WHERE membership_id LIKE '48Z%' AND check_in_date = '20180109';

membership_id	check_in_date	check_in_time	check_out_time
48Z7A	         20180109	     1600	         1730
48Z55	         20180109	     1530	         1700

-- pista 9 --

SELECT p.id, p.name, dl.plate_number
FROM person p
JOIN drivers_license dl ON p.license_id = dl.id
WHERE dl.plate_number LIKE '%H42W%';

id	    name	        plate_number
51739	Tushar Chandra	4H42WR
67318	Jeremy Bowers	0H42W2
78193	Maxine Whitely	H42W0X

-- pista 10 --

SELECT *
FROM get_fit_now_member
WHERE person_id IN (51739, 67318, 78193) AND id LIKE '48Z%' AND membership_status = 'gold';

id	    person_id	name	        membership_start_date	membership_status
48Z55	67318	    eremy Bowers	20160101	            gold

-- Solution --

INSERT INTO solution VALUES (1, 'Jeremy Bowers');
        
        SELECT value FROM solution;

value
Congrats, you found the murderer! But wait, there's more... If you think you're up for a challenge, try querying the interview transcript of the murderer to find the real villain behind this crime. If you feel especially confident in your SQL skills, try to complete this final step with no more than 2 queries. Use this same INSERT statement with your new suspect to check your answer.