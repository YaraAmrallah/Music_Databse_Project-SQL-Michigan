/* Create Database and its tables */

CREATE DATABASE Music
DEFAULT CHARACTER SET utf8;


USE Music;


CREATE TABLE Artist (
artist_id INTEGER NOT NULL AUTO_INCREMENT,
name VARCHAR(255),
PRIMARY KEY(artist_id)
) ENGINE = InnoDB;


CREATE TABLE Album (
album_id INTEGER NOT NULL AUTO_INCREMENT,
title VARCHAR(255),
artist_id INTEGER,

PRIMARY KEY(album_id),
INDEX USING BTREE(title),

CONSTRAINT FOREIGN KEY(artist_id)
REFERENCES Artist(artist_id)
ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE = InnoDB;


CREATE TABLE Genre (
genre_id INTEGER NOT NULL AUTO_INCREMENT,
name VARCHAR(255),
PRIMARY KEY(genre_id),
INDEX USING BTREE(name)
) ENGINE = InnoDB;



CREATE TABLE Track (
track_id INTEGER NOT NULL AUTO_INCREMENT,
title VARCHAR(255),
len INTEGER,
rating INTEGER,
count INTEGER,
album_id INTEGER,
genre_id INTEGER,

PRIMARY KEY(track_id),
INDEX USING BTREE(title),

CONSTRAINT FOREIGN KEY(album_id)
REFERENCES Album(album_id)
ON DELETE CASCADE ON UPDATE CASCADE,

CONSTRAINT FOREIGN KEY(genre_id)
REFERENCES Genre(genre_id)
ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE = InnoDB;


/* Fill Database */
/* Artist Table */
INSERT INTO Artist (name) VALUES ('Amr Diab');
INSERT INTO Artist (name) VALUES ('Wegz');
INSERT INTO Artist (name) VALUES ('Halim');

/* Genre Table */
INSERT INTO Genre (name) VALUES ('Rap');
INSERT INTO Genre (name) VALUES ('Trap');
INSERT INTO Genre (name) VALUES ('Pop');
INSERT INTO Genre (name) VALUES ('Tarab');

/* Album Table */
INSERT INTO Album (title,artist_id) VALUES ('Sahran',1);
INSERT INTO Album (title,artist_id) VALUES ('Ana Gheir',1);
INSERT INTO Album (title,artist_id) VALUES ('Random',2);
INSERT INTO Album (title,artist_id) VALUES ('Halim 1', 3);
INSERT INTO Album (title,artist_id) VALUES ('Halim 2', 3);

/* Track Table */
INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('Gamda Bas',5,300,562,1,3);

INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('Sahran',5,300,562,1,3);


INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('Hayeish Yeftekerni',5,300,562,1,3);


INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('Gamila',5,300,562,1,3);


INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('Bel Dehka Di',5,300,562,1,3);


INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('Makanak fi Alby',5,300,562,1,3);


INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('Mahragan',5,400,562,1,3);


INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('Helwa el Bedayat',5,372,562,1,3);


INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('Rooh',5,350,562,1,3);


INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('Bahebo',5,250,562,2,3);

INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('Youm Talat',5,250,562,2,3);

INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('Da law etsab',5,250,562,2,3);

INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('Dorak Gai',5,420,562,3,1);

INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('El Ghasala',5,420,562,3,2);

INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('Seni 20',5,420,562,3,2);

INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('Ouloulo',5,1000,1000,4,4);

INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('Kare2et Al Fengan',5,1050,1500,4,4);

INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('Ahwak',5,1025,6151,5,4);

INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('Sawah',5,1000,1000,5,4);

INSERT INTO Track (title,rating,len,count,album_id,genre_id) 
VALUES ('El Helwa',5,1000,1000,5,4);


/* JOIN Queries */
/*  all the data joined up sorted in ascending order by the album title */
SELECT Track.title, Artist.name, Album.title, Genre.name
FROM Track JOIN Genre JOIN Album JOIN Artist ON
Track.genre_id = Genre.genre_id AND Track.album_id = Album.album_id AND Album.artist_id = Artist.artist_id
ORDER BY Genre.name ASC;

/* all of the genres for a particular artist */
SELECT DISTINCT Artist.name, Genre.name 
FROM Artist JOIN Genre JOIN Album JOIN Track
ON Track.genre_id = Genre.genre_id AND Track.album_id = Album.album_id AND Album.artist_id = Artist.artist_id
WHERE Artist.name = 'Wegz'


/* Come up with a query using GROUP BY to show the number of tracks an Artist has in each Genre */
SELECT Artist.name, Genre.name, COUNT(Track.genre_id)
FROM Artist JOIN Genre JOIN Track JOIN Album
ON Track.genre_id = Genre.genre_id AND Track.album_id = Album.album_id AND Album.artist_id = Artist.artist_id
GROUP BY Genre.name
ORDER BY Artist.name, COUNT(Track.genre_id) DESC
