# Solution

### 1. Retrieve the crime scene report
Started with the date, type, and city given in the prompt.

```sql
SELECT *
FROM crime_scene_report
WHERE type = 'murder' AND city = 'SQL City' AND date = 20180115;
```

| date     | type   | description                                                                                                                                             | city     |
|----------|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| 20180115 | murder | Security footage shows that there were 2 witnesses. The first witness lives at the last house on "Northwestern Dr". The second witness, named Annabel, lives somewhere on "Franklin Ave". | SQL City |

The report points to two witnesses:
- someone at the **last house on Northwestern Dr**
- **Annabel** on **Franklin Ave**

---

### 2. Find the first witness
Sorted Northwestern Dr in descending order to get the last house.

```sql
SELECT *
FROM person
WHERE address_street_name = 'Northwestern Dr'
ORDER BY address_number DESC;
```

| id    | name            | license_id | address_number | address_street_name | ssn       |
|-------|-----------------|------------|----------------|---------------------|-----------|
| 14887 | Morty Schapiro  | 118009     | 4919           | Northwestern Dr     | 111564949 |

---

### 3. Find the second witness

```sql
SELECT *
FROM person
WHERE address_street_name = 'Franklin Ave' AND name LIKE 'Annabel%';
```

| id    | name            | license_id | address_number | address_street_name | ssn       |
|-------|-----------------|------------|----------------|---------------------|-----------|
| 16371 | Annabel Miller  | 490173     | 103            | Franklin Ave        | 318771143 |

---

### 4. Read both interviews

```sql
SELECT *
FROM interview
WHERE person_id IN (14887, 16371);
```

| person_id | transcript |
|-----------|------------|
| 14887 | I heard a gunshot and then saw a man run out. He had a "Get Fit Now Gym" bag. The membership number on the bag started with "48Z". Only gold members have those bags. The man got into a car with a plate that included "H42W". |
| 16371 | I saw the murder happen, and I recognized the killer from my gym when I was working out last week on January the 9th. |

From the interviews, the useful clues were:
- **Get Fit Now Gym**
- membership starting with **48Z**
- **gold** member
- gym visit on **2018-01-09**
- car plate containing **H42W**

---

### 5. Narrow down gym members
Used the membership prefix, membership type, and check-in date.

```sql
SELECT m.person_id, m.name, c.membership_id, m.membership_status, c.check_in_date
FROM get_fit_now_member AS m
JOIN get_fit_now_check_in AS c ON m.id = c.membership_id
WHERE m.id LIKE '48Z%' AND m.membership_status = 'gold' AND check_in_date = 20180109;
```

| person_id | name           | membership_id | membership_status | check_in_date |
|-----------|----------------|---------------|-------------------|---------------|
| 28819     | Joe Germuska   | 48Z7A         | gold              | 20180109      |
| 67318     | Jeremy Bowers  | 48Z55         | gold              | 20180109      |

This reduced the list to two suspects.

---

### 6. Match the license plate clue
Joined the suspect list to `person` and `drivers_license` to check the partial plate.

```sql
SELECT m.person_id, m.name, c.membership_id, m.membership_status, c.check_in_date, p.license_id, d.plate_number
FROM get_fit_now_member AS m
JOIN get_fit_now_check_in AS c ON m.id = c.membership_id
JOIN person AS p ON m.person_id = p.id
JOIN drivers_license AS d ON p.license_id = d.id
WHERE m.id LIKE '48Z%' AND m.membership_status = 'gold' AND check_in_date = 20180109;
```

| person_id | name           | membership_id | membership_status | check_in_date | license_id | plate_number |
|-----------|----------------|---------------|-------------------|---------------|------------|--------------|
| 67318     | Jeremy Bowers  | 48Z55         | gold              | 20180109      | 423327     | 0H42W2       |

So the murderer is **Jeremy Bowers**.

---

### 7. Check the solution
Finally, verified the answer using the provided `solution` table.

```sql
INSERT INTO solution VALUES (1, 'Jeremy Bowers');

SELECT value FROM solution;
```

| value |
|-------|
| Congrats, you found the murderer! But wait, there's more... If you think you're up for a challenge, try querying the interview transcript of the murderer to find the real villain behind this crime. If you feel especially confident in your SQL skills, try to complete this final step with no more than 2 queries. Use this same INSERT statement with your new suspect to check your answer. |

---

## 8. Interview the murderer
Used Jeremy Bowers’ ID to get more details about who hired him.

```sql
SELECT *
FROM interview
WHERE person_id = 67318;
```

| person_id | transcript |
|-----------|------------|
| 67318 | I was hired by a woman with a lot of money. I don't know her name but I know she's around 5'5" (65") or 5'7" (67"). She has red hair and she drives a Tesla Model S. I know that she attended the SQL Symphony Concert 3 times in December 2017. |

Key clues:
- female
- height between **65–67 inches**
- **red hair**
- drives a **Tesla Model S**
- attended **SQL Symphony Concert 3 times in Dec 2017**

---

## 9. Find concert attendees
Filtered people who attended the concert exactly 3 times in December 2017.

```sql
SELECT person_id, COUNT(*) AS freq
FROM facebook_event_checkin
WHERE event_name = 'SQL Symphony Concert' AND date LIKE '201712%'
GROUP BY person_id
HAVING freq = 3;
```

| person_id | freq |
|-----------|------|
| 24556     | 3    |
| 99716     | 3    |

---

## 10. Match physical and car details
Joined with `drivers_license` and `person` to apply remaining filters.

```sql
SELECT p.id, p.name, p.license_id, d.height, d.hair_color, d.car_make, d.car_model
FROM drivers_license AS d
JOIN person AS p ON d.id = p.license_id
WHERE hair_color = 'red' AND height BETWEEN 65 AND 67 AND car_make = 'Tesla'
  AND car_model = 'Model S' AND p.id IN (24556, 99716);
```

| id    | name              | license_id | height | hair_color | car_make | car_model |
|-------|-------------------|------------|--------|------------|----------|-----------|
| 99716 | Miranda Priestly  | 202298     | 66     | red        | Tesla    | Model S   |

This matches all clues → **Miranda Priestly**.

---

## 11. Final answer

```sql
INSERT INTO solution VALUES (1, 'Miranda Priestly');

SELECT value FROM solution;
```

| value |
|-------|
| Congrats, you found the brains behind the murder! Everyone in SQL City hails you as the greatest SQL detective of all time. Time to break out the champagne! |

The mastermind behind the crime is **Miranda Priestly**.
