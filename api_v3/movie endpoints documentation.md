## Movie endpoints documentation.


### GET /api/v3/movies/categories
Get a list of featured content arranged by categories. The response movie data accounts for the logged-in user.

#### Fields
* __categories__ - collection of featured categories each having 

	* __title__
	* __movies__ - collection of movies in the category each having
		* __title__
		* __description__ - short description / synopsis
		* __year__ - year of release
		* __genre__
		* __poster_url__
		* __pg_rating__ - parental guidelines rating ([MPAA](http://www.mpaa.org/film-ratings/))
		* __queue_count__ - number of users who have the movie in their queue
		* __url__ - movie's GoWatchIt URL
		* __providers__ - list of providers that currently have the movie available

>! Spoiler 1
>! Spoiler 2

### GET /api/v3/movies/:id
Get metadata and availabilities for a movie.

#### Fields
* __id__ - movie's GoWatchIt ID
* __description__ - short description / synopsis
* __title__
* __poster_url__ 
* __year__ - year of release
* __genre__
* __pg_rating__ - parental guidelines rating ([MPAA](http://www.mpaa.org/film-ratings/)) 
* __duration__ 
* __queue_count__ - number of users who have the movie in their queue
* __url__ - movie's GoWatchIt URL
* __contributors__ - contributors such as director, writers, cast members etc.
* __trailer_url__ 
* __special_caption__ reserved for displaying customized availability information.
* __providers__ - list of providers that currently have the movie available 
* __available__ - boolean flag indicating movie's availability status

### GET /api/v3/movies/:id/availabilities
Get availabilities for a movie.
