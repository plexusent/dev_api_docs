## Movie endpoints documentation.


### GET /api/v3/movies/categories
Get a list of featured content arranged by categories. The response movie data accounts for the logged-in user.

* __Fields__
* __categories__ - a collections of featured categories with each category having 

	* __title__ the category title
	* __movies__ - a collection of movies in the category with each movie having
		* __title__
		* __description__
		* __year__
		* __genre_
		* __poster_url__
		* __pg_rating__ - parental guidelines rating
		* __queue_count__ - the number of queues the movie is in
		* __url__ - the GoWatchIt url
		* __providers__ - a list of provider logos that currently carry the movie


### GET /api/v3/movies/:id
Get metadata and availabilities for a movie.

### GET /api/v3/movies/:id/availabilities
Get availabilities for a movie.
