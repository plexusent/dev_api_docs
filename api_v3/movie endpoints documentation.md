## Movie endpoints documentation.


### GET /api/v3/movies/categories
Get a list of featured content arranged by categories. The response movie data accounts for the logged-in user.

#### Fields
* __categories__ - a collection of featured categories each having 

	* __title__
	* __movies__ - a collection of movies in the category each having
		* __title__
		* __description__ - short description / synopsis
		* __year__ - year of the release
		* __genre__
		* __poster_url__
		* __pg_rating__ - parental guidelines rating ([MPAA](http://www.mpaa.org/film-ratings/))
		* __queue_count__ - the number of queues the movie is in
		* __url__ - movie's GoWatchIt url
		* __providers__ - a list of providers that currently have the movie available


### GET /api/v3/movies/:id
Get metadata and availabilities for a movie.

#### Fields
Each movie will have

* __id__ - the movie's GoWatchIt id
* __description__ - a synopsis
* __title__
* __poster_url__ 
* __year_url__
* __genre__
* __pg_rating__
* __duration__
* __queue_count__
* __url__
* __contributors__
* __trailer_url__
* __special_caption__
* __providers__
* __available__

### GET /api/v3/movies/:id/availabilities
Get availabilities for a movie.
