## Exercises

### 1. Create a Songs Table

This table should be called `songs` and have four properties with these exact names.
1. `id`: An integer that is the primary key, and auto increments.
2. `name`: A string that cannot be null.
3. `length`: A float that represents the length of the song in minutes that cannot be null.
4. `album_id`: An integer that is a foreign key referencing the albums table that cannot be null.

After successfully creating the table copy the code from [data.sql](data.sql) into MySQL Workbench, and run it to populate all of the data for the rest of the exercises.

```sql
CREATE TABLE songs (
  id INT NOT NULL AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL,
  length FLOAT NOT NULL,
  album_id INT NOT NULL,
  PRIMARY KEY (id),
  FOREIGN KEY (album_id) REFERENCES albums(id)
);

SELECT * FROM songs;
```

| id  | name                                            | length     | album_id |
| --- | ----------------------------------------------- | ---------- | -------- |
| 1   | Arrival                                         | 1.5        | 1        |
| 2   | The Everones                                    | 6.2166667  | 1        |
| 3   | Dream Machines                                  | 5.633333   | 1        |
| 4   | Against the Grain                               | 6.9666667  | 1        |
| 5   | Victorious                                      | 4.9166665  | 1        |
| 6   | Tiara's Song (Farewell Pt. 1)                   | 7.266667   | 1        |
| 7   | Goodnight (Farewell Pt. 2)                      | 7.1666665  | 1        |
| 8   | Beyond Today (Farewell Pt. 3)                   | 5.1        | 1        |
| 9   | The Truth                                       | 4.2833333  | 1        |
| 10  | By the Light of the Funeral Pyres               | 3.9        | 1        |
| 11  | Damnation Below                                 | 6.733333   | 1        |
| 12  | Procession                                      | 0.75       | 1        |
| 13  | Exhale                                          | 9.5        | 1        |
| 14  | Wiseman                                         | 5.7        | 2        |
| 15  | Alley Cat                                       | 6.1        | 2        |
| 16  | The Angelmaker                                  | 8.483334   | 2        |
| 17  | King of Whitewater                              | 7.3333335  | 2        |
| 18  | Long Way Home                                   | 4.4333334  | 2        |
| 19  | Move on Through                                 | 5.0666666  | 2        |
| 20  | The Great Escape                                | 30.233334  | 2        |
| 21  | A New Beginning                                 | 3.0833333  | 3        |
| 22  | There and Back                                  | 3.0333333  | 3        |
| 23  | Welcome to Mercy Falls                          | 5.1833334  | 3        |
| 24  | Unbreakable                                     | 7.3166666  | 3        |
| 25  | Tears for a Father                              | 1.9666667  | 3        |
| 26  | A Day Away                                      | 3.7166667  | 3        |
| 27  | Tears for a Son                                 | 1.7        | 3        |
| 28  | Paradise                                        | 5.766667   | 3        |
| 29  | Fall in Line                                    | 6.15       | 3        |
| 30  | Break the Silence                               | 9.483334   | 3        |
| 31  | Hide and Seek                                   | 7.766667   | 3        |
| 32  | Destiny Calls                                   | 6.3        | 3        |
| 33  | One Last Goodbye                                | 4.35       | 3        |
| 34  | Back in Time                                    | 1.2333333  | 3        |
| 35  | The Black Parade                                | 6.95       | 3        |
| 36  | Battery                                         | 5.2166667  | 4        |
| 37  | Master of Puppets                               | 8.583333   | 4        |
| 38  | The Thing That Should Not Be                    | 6.6        | 4        |
| 39  | Welcome Home (Sanitarium)                       | 6.45       | 4        |
| 40  | Disposable Heroes                               | 8.283334   | 4        |
| 41  | Leper Messiah                                   | 5.6666665  | 4        |
| 42  | Orion                                           | 8.45       | 4        |
| 43  | Damage Inc.                                     | 5.5333333  | 4        |
| 44  | Blackened                                       | 6.6833334  | 5        |
| 45  | ...And Justice for All                          | 9.783334   | 5        |
| 46  | Eye of the Beholder                             | 6.5        | 5        |
| 47  | One                                             | 7.45       | 5        |
| 48  | The Shortest Straw                              | 6.6        | 5        |
| 49  | Harvester of Sorrow                             | 5.766667   | 5        |
| 50  | The Frayed Ends of Sanity                       | 7.733333   | 5        |
| 51  | To Live Is to Die                               | 9.816667   | 5        |
| 52  | Dyers Eve                                       | 5.2166667  | 5        |
| 53  | That Was Just Your Life                         | 7.133333   | 6        |
| 54  | The End of the Line                             | 7.866667   | 6        |
| 55  | Broken Beat & Scarred                           | 6.4166665  | 6        |
| 56  | The Day That Never Comes                        | 7.9333334  | 6        |
| 57  | All Nightmare Long                              | 7.9666667  | 6        |
| 58  | Cyanide                                         | 6.6666665  | 6        |
| 59  | The Unforgiven III                              | 7.7833333  | 6        |
| 60  | The Judas Kiss                                  | 8.016666   | 6        |
| 61  | Suicide & Redemption                            | 9.966666   | 6        |
| 62  | My Apocalypse                                   | 5.016667   | 6        |
| 63  | Shamayim                                        | 1.8833333  | 7        |
| 64  | Firmament                                       | 7.483333   | 7        |
| 65  | The First Commandment of the Luminaries         | 6.7833333  | 7        |
| 66  | Ptolemy Was Wrong                               | 6.4666667  | 7        |
| 67  | Metaphysics of the Hangman                      | 5.6833334  | 7        |
| 68  | Catharsis of a Heretic                          | 2.1333334  | 7        |
| 69  | Swallowed by the Earth                          | 4.983333   | 7        |
| 70  | Epiphany                                        | 3.6166666  | 7        |
| 71  | The Origin of Species                           | 7.383333   | 7        |
| 72  | The Origin of God                               | 4.55       | 7        |
| 73  | Epipelagic                                      | 1.2        | 8        |
| 74  | Mesopelagic: Into the Uncanny                   | 5.9333334  | 8        |
| 75  | Bathyalpelagic I: Impasses                      | 4.4        | 8        |
| 76  | Bathyalpelagic II: The Wish in Dreams           | 3.3        | 8        |
| 77  | Bathyalpelagic III: Disequilibrated             | 4.45       | 8        |
| 78  | Abyssopelagic I: Boundless Vasts                | 3.45       | 8        |
| 79  | Abyssopelagic II: Signals of Anxiety            | 5.0833335  | 8        |
| 80  | Hadopelagic I: Omen of the Deep                 | 1.1166667  | 8        |
| 81  | Hadopelagic II: Let Them Believe                | 9.283334   | 8        |
| 82  | Demersal: Cognitive Dissonance                  | 9.083333   | 8        |
| 83  | Benthic: The Origin of Our Wishes               | 5.9166665  | 8        |
| 84  | Anthropocentric                                 | 9.4        | 9        |
| 85  | The Grand Inquisitor I: Karamazov Baseness      | 5.0333333  | 9        |
| 86  | She Was the Universe                            | 5.65       | 9        |
| 87  | For He That Wavereth...                         | 2.1166666  | 9        |
| 88  | The Grand Inquisitor II: Roots & Locusts        | 6.55       | 9        |
| 89  | The Grand Inquisitor III: A Tiny Grain of Faith | 1.9333333  | 9        |
| 90  | Sewers of the Soul                              | 3.7333333  | 9        |
| 91  | Wille zum Untergang                             | 6.05       | 9        |
| 92  | Heaven TV                                       | 5.0666666  | 9        |
| 93  | The Almightiness Contradiction                  | 4.5666666  | 9        |
| 94  | The Reckoning                                   | 4.1833334  | 10       |
| 95  | Endless War                                     | 4.15       | 10       |
| 96  | Raise Your Banner                               | 5.5666666  | 10       |
| 97  | Supernova                                       | 5.5666666  | 10       |
| 98  | Holy Ground                                     | 4.1666665  | 10       |
| 99  | In Vain                                         | 4.4166665  | 10       |
| 100 | Firelight                                       | 4.766667   | 10       |
| 101 | Mad World                                       | 4.95       | 10       |
| 102 | Mercy Mirror                                    | 3.8166666  | 10       |
| 103 | Trophy Hunter                                   | 5.85       | 10       |
| 104 | Why Not Me                                      | 0.56666666 | 11       |
| 105 | Shot in the Dark                                | 5.0333333  | 11       |
| 106 | In the Middle of the Night                      | 5.1833334  | 11       |
| 107 | Faster                                          | 4.383333   | 11       |
| 108 | Fire and Ice                                    | 3.95       | 11       |
| 109 | Iron                                            | 5.6666665  | 11       |
| 110 | Where Is the Edge                               | 3.9833333  | 11       |
| 111 | Sinéad                                          | 4.383333   | 11       |
| 112 | Lost                                            | 5.233333   | 11       |
| 113 | Murder                                          | 4.266667   | 11       |
| 114 | A Demon's Fate                                  | 5.5        | 11       |
| 115 | Stairway to the Skies                           | 5.5333333  | 11       |
| 116 | Restless                                        | 6.133333   | 12       |
| 117 | Enter                                           | 7.25       | 12       |
| 118 | Pearls of Light                                 | 5.25       | 12       |
| 119 | Deep Within                                     | 4.5        | 12       |
| 120 | Gatekeeper                                      | 6.7166667  | 12       |
| 121 | Grace                                           | 5.1666665  | 12       |
| 122 | Blooded                                         | 3.6333334  | 12       |
| 123 | Candles                                         | 7.116667   | 12       |
| 124 | Scavenger of Human Sorrow                       | 6.9333334  | 13       |
| 125 | Bite the Pain                                   | 4.483333   | 13       |
| 126 | Spirit Crusher                                  | 6.7833333  | 13       |
| 127 | Story to Tell                                   | 6.5666666  | 13       |
| 128 | Flesh and the Power It Holds                    | 8.433333   | 13       |
| 129 | Voice of the Soul                               | 3.7166667  | 13       |
| 130 | To Forgive Is to Suffer                         | 5.9166665  | 13       |
| 131 | A Moment of Clarity                             | 7.4166665  | 13       |
| 132 | Painkiller                                      | 6.0333333  | 13       |
| 133 | Overactive Imagination                          | 3.5        | 14       |
| 134 | In Human Form                                   | 3.95       | 14       |
| 135 | Jealousy                                        | 3.6833334  | 14       |
| 136 | Trapped in a Corner                             | 4.233333   | 14       |
| 137 | Nothing Is Everything                           | 3.3166666  | 14       |
| 138 | Mentally Blind                                  | 4.8166666  | 14       |
| 139 | Individual Thought Patterns                     | 4.016667   | 14       |
| 140 | Destiny                                         | 4.1        | 14       |
| 141 | Out of Touch                                    | 4.366667   | 14       |
| 142 | The Philosopher                                 | 4.2166667  | 14       |
| 143 | Flattening of Emotions                          | 4.4666667  | 15       |
| 144 | Suicide Machine                                 | 4.383333   | 15       |
| 145 | Together as One                                 | 4.1666665  | 15       |
| 146 | Secret Face                                     | 4.65       | 15       |
| 147 | Lack of Comprehension                           | 3.7166667  | 15       |
| 148 | See Through Dreams                              | 4.65       | 15       |
| 149 | Cosmic Sea                                      | 4.45       | 15       |
| 150 | Vacant Planets                                  | 3.8666666  | 15       |
| 151 | Stora Rövardansen                               | 1.55       | 16       |
| 152 | King                                            | 3.7333333  | 16       |
| 153 | The Mission                                     | 4.3        | 16       |
| 154 | Lifetime                                        | 4.8166666  | 16       |
| 155 | Rain                                            | 4.05       | 16       |
| 156 | She's Alive                                     | 4.2        | 16       |
| 157 | I Stand Alone                                   | 4.733333   | 16       |
| 158 | Starlight                                       | 4.6666665  | 16       |
| 159 | Battery                                         | 5.2166667  | 16       |
| 160 | If I Die in Battle                              | 4.766667   | 17       |
| 161 | The Seller of Souls                             | 3.4        | 17       |
| 162 | Primo Victoria                                  | 3.7333333  | 17       |
| 163 | Dangers in My Head                              | 4.0833335  | 17       |
| 164 | Black Wings of Hate                             | 4.6833334  | 17       |
| 165 | Bed of Nails                                    | 3.6166666  | 17       |
| 166 | Spelled in Waters                               | 4.4333334  | 17       |
| 167 | Neuer Wind                                      | 3.35       | 17       |
| 168 | The Higher Flight                               | 5          | 17       |
| 169 | Master of the Wind                              | 6.15       | 17       |
| 170 | Lost Forever                                    | 4.733333   | 18       |
| 171 | To Sing a Metal Song                            | 3.4        | 18       |
| 172 | One to Ten                                      | 4.1        | 18       |
| 173 | I Am Human                                      | 3.9333334  | 18       |
| 174 | My Voice                                        | 5.5        | 18       |
| 175 | Rebellion                                       | 4.0833335  | 18       |
| 176 | Last Night of the Kings                         | 3.8666666  | 18       |
| 177 | Tribe of Force                                  | 3.2833333  | 18       |
| 178 | Water Fire Heaven Earth                         | 3.5333333  | 18       |
| 179 | Master of Puppets                               | 8.383333   | 18       |
| 180 | Magic Taborea                                   | 3.3666666  | 18       |
| 181 | Hearted                                         | 4          | 18       |
| 182 | Frodo's Dream                                   | 3.1        | 18       |

---

### 2. Select only the Names of all the Bands

Change the name of the column the data returns to `Band Name`.

```sql
SELECT name AS 'Band Name' FROM bands;
```

| Band Name         |
| ----------------- |
| Seventh Wonder    |
| Metallica         |
| The Ocean         |
| Within Temptation |
| Death             |
| Van Canto         |
| Dream Theater     |

---

### 3. Select the Oldest Album

Make sure to only return one result from this query, and that you are not returning any albums that do not have a release year.

```sql
SELECT * FROM albums
WHERE release_year IS NOT NULL
ORDER BY release_year
LIMIT 1;
```

| id  | name                   | release_year | band_id |
| --- | ---------------------- | ------------ | ------- |
| 5   | ...And Justice for All | 1988         | 2       |

---

### 4. Get all Bands that have Albums

Return the band name as `Band Name`.

```sql
SELECT DISTINCT b.name AS 'Band Name'
FROM albums AS a
JOIN bands AS b ON a.band_id = b.id;
```

| Band Name         |
| ----------------- |
| Seventh Wonder    |
| Metallica         |
| The Ocean         |
| Within Temptation |
| Death             |
| Van Canto         |

---

### 5. Get all Bands that have No Albums

Return the band name as `Band Name`.

```sql
SELECT name AS 'Band Name' FROM bands
WHERE id NOT IN (SELECT band_id FROM albums);
```

| Band Name     |
| ------------- |
| Dream Theater |

---

### 6. Get the Longest Album

Return the album name as `Name`, the album release year as `Release Year`, and the album length as `Duration`.

```sql
SELECT a.name AS Name, a.release_year AS 'Release Year', SUM(s.length) AS Duration
FROM albums AS a
JOIN songs AS s ON a.id = s.album_id
GROUP BY a.name, a.release_year
ORDER BY Duration DESC
LIMIT 1;
```

| Name           | Release Year | Duration          |
| -------------- | ------------ | ----------------- |
| Death Magnetic | 2008         | 74.76666593551636 |

---

### 7. Update the Release Year of the Album with no Release Year

Set the release year to 1986.
    
```sql    
UPDATE albums
SET release_year = 1986
WHERE release_year IS NULL;

SELECT * FROM albums;
```
DB fiddle allows you to use `release_year IS NULL`.

| id  | name                        | release_year | band_id |
| --- | --------------------------- | ------------ | ------- |
| 1   | Tiara                       | 2018         | 1       |
| 2   | The Great Escape            | 2010         | 1       |
| 3   | Mercy Falls                 | 2008         | 1       |
| 4   | Master of Puppets           | 1986         | 2       |
| 5   | ...And Justice for All      | 1988         | 2       |
| 6   | Death Magnetic              | 2008         | 2       |
| 7   | Heliocentric                | 2010         | 3       |
| 8   | Pelagial                    | 2013         | 3       |
| 9   | Anthropocentric             | 2010         | 3       |
| 10  | Resist                      | 2018         | 4       |
| 11  | The Unforgiving             | 2011         | 4       |
| 12  | Enter                       | 1997         | 4       |
| 13  | The Sound of Perseverance   | 1998         | 5       |
| 14  | Individual Thought Patterns | 1993         | 5       |
| 15  | Human                       | 1991         | 5       |
| 16  | A Storm to Come             | 2006         | 6       |
| 17  | Break the Silence           | 2011         | 6       |
| 18  | Tribe of Force              | 2010         | 6       |

---

### 8. Insert a record for your favorite Band and one of their Albums

```sql
INSERT INTO bands(name) VALUES ('Coldplay');

SELECT * FROM bands;
```

| id  | name              |
| --- | ----------------- |
| 1   | Seventh Wonder    |
| 2   | Metallica         |
| 3   | The Ocean         |
| 4   | Within Temptation |
| 5   | Death             |
| 6   | Van Canto         |
| 7   | Dream Theater     |
| 8   | Coldplay          |

```sql
INSERT INTO albums(name, release_year, band_id) VALUES ('Parachutes', 2000, 8);

SELECT * FROM albums;
```

| id  | name                        | release_year | band_id |
| --- | --------------------------- | ------------ | ------- |
| 1   | Tiara                       | 2018         | 1       |
| 2   | The Great Escape            | 2010         | 1       |
| 3   | Mercy Falls                 | 2008         | 1       |
| 4   | Master of Puppets           | 1986         | 2       |
| 5   | ...And Justice for All      | 1988         | 2       |
| 6   | Death Magnetic              | 2008         | 2       |
| 7   | Heliocentric                | 2010         | 3       |
| 8   | Pelagial                    | 2013         | 3       |
| 9   | Anthropocentric             | 2010         | 3       |
| 10  | Resist                      | 2018         | 4       |
| 11  | The Unforgiving             | 2011         | 4       |
| 12  | Enter                       | 1997         | 4       |
| 13  | The Sound of Perseverance   | 1998         | 5       |
| 14  | Individual Thought Patterns | 1993         | 5       |
| 15  | Human                       | 1991         | 5       |
| 16  | A Storm to Come             | 2006         | 6       |
| 17  | Break the Silence           | 2011         | 6       |
| 18  | Tribe of Force              | 2010         | 6       |
| 19  | Parachutes                  | 2000         | 8       |

---

### 9. Delete the Band and Album you added in #8

```sql
DELETE FROM albums WHERE id = 19;

SELECT * FROM albums;
```

| id  | name                        | release_year | band_id |
| --- | --------------------------- | ------------ | ------- |
| 1   | Tiara                       | 2018         | 1       |
| 2   | The Great Escape            | 2010         | 1       |
| 3   | Mercy Falls                 | 2008         | 1       |
| 4   | Master of Puppets           | 1986         | 2       |
| 5   | ...And Justice for All      | 1988         | 2       |
| 6   | Death Magnetic              | 2008         | 2       |
| 7   | Heliocentric                | 2010         | 3       |
| 8   | Pelagial                    | 2013         | 3       |
| 9   | Anthropocentric             | 2010         | 3       |
| 10  | Resist                      | 2018         | 4       |
| 11  | The Unforgiving             | 2011         | 4       |
| 12  | Enter                       | 1997         | 4       |
| 13  | The Sound of Perseverance   | 1998         | 5       |
| 14  | Individual Thought Patterns | 1993         | 5       |
| 15  | Human                       | 1991         | 5       |
| 16  | A Storm to Come             | 2006         | 6       |
| 17  | Break the Silence           | 2011         | 6       |
| 18  | Tribe of Force              | 2010         | 6       |

```sql
DELETE FROM bands WHERE id = 8;

SELECT * FROM bands;
```

| id  | name              |
| --- | ----------------- |
| 1   | Seventh Wonder    |
| 2   | Metallica         |
| 3   | The Ocean         |
| 4   | Within Temptation |
| 5   | Death             |
| 6   | Van Canto         |
| 7   | Dream Theater     |

---

### 10. Get the Average Length of all Songs

Return the average length as `Average Song Duration`.

```sql
SELECT AVG(length) AS 'Average Song Duration'
FROM songs;
```

| Average Song Duration |
| --------------------- |
| 5.352472513259112     |

---

### 11. Select the longest Song off each Album

Return the album name as `Album`, the album release year as `Release Year`, and the longest song length as `Duration`.

```sql
SELECT DISTINCT a.name AS Album, a.release_year AS 'Release Year',
MAX(s.length) AS Duration
FROM albums AS a
JOIN songs AS s ON a.id = s.album_id
GROUP BY a.name, a.release_year;
```

| Album                       | Release Year | Duration  |
| --------------------------- | ------------ | --------- |
| Tiara                       | 2018         | 9.5       |
| The Great Escape            | 2010         | 30.233334 |
| Mercy Falls                 | 2008         | 9.483334  |
| Master of Puppets           | 1986         | 8.583333  |
| ...And Justice for All      | 1988         | 9.816667  |
| Death Magnetic              | 2008         | 9.966666  |
| Heliocentric                | 2010         | 7.483333  |
| Pelagial                    | 2013         | 9.283334  |
| Anthropocentric             | 2010         | 9.4       |
| Resist                      | 2018         | 5.85      |
| The Unforgiving             | 2011         | 5.6666665 |
| Enter                       | 1997         | 7.25      |
| The Sound of Perseverance   | 1998         | 8.433333  |
| Individual Thought Patterns | 1993         | 4.8166666 |
| Human                       | 1991         | 4.65      |
| A Storm to Come             | 2006         | 5.2166667 |
| Break the Silence           | 2011         | 6.15      |
| Tribe of Force              | 2010         | 8.383333  |

---

### 12. Get the number of Songs for each Band

Return the band name as `Band`, the number of songs as `Number of Songs`.

```sql
SELECT b.name AS Band, COUNT(s.id) AS 'Number of Songs'
FROM bands AS b
JOIN albums AS a ON b.id = a.band_id
JOIN songs AS s ON a.id = s.album_id
GROUP BY b.name;
```

| Band              | Number of Songs |
| ----------------- | --------------- |
| Seventh Wonder    | 35              |
| Metallica         | 27              |
| The Ocean         | 31              |
| Within Temptation | 30              |
| Death             | 27              |
| Van Canto         | 32              |
