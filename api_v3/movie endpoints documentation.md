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
		* __run_time__


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
* __run_time__ 
* __queue_count__ - number of users who have the movie in their queue
* __url__ - movie's GoWatchIt URL
* __contributors__ - movie contributors such as director, writers, cast members etc. grouped by role
* __trailer_url__ 
* __special_caption__ reserved for displaying customized availability information.
* __current_providers__ - a brief list of providers that currently have the movie available 
* __available__ - boolean flag indicating movie's availability status
* __availabilities__ - a collection of movie availabilities

Each availability encapsulates
* __format_line__ - formatted list of formats in which movie is available for a particular provider. Ex: "SD / HD"
* __buy_line__ - formatted buy line such as "Buy from $9.99"
* __rent_line__ - formatted rent line such as "Rent from $3.99"
* __provider_name__ - name of provider
* __provider_format_logos__ - provider-format logos (such as Netflix Mail and Netflix Streaming)
	* __light__
	* __dark__
* __provider_format_id__ - provider-format's GoWatchIt ID
* __watch_now_url__ - provider URL to the movie via GoWatchIt  
* __category__ - avilabilitie's category such as dvd, online, presale or theater.


### GET /api/v3/movies/:id/availabilities
Get availabilities for a movie. A lighter version of GET movies/:id that skips movie metadata and only returns availabilities.

#### Fields

* __availabilities__ - a collection of movie availabilities

Each availability encapsulates
* __format_line__ - formatted list of formats in which movie is available for a particular provider. Ex: "SD / HD"
* __buy_line__ - formatted buy line such as "Buy from $9.99"
* __rent_line__ - formatted rent line such as "Rent from $3.99"
* __provider_name__ - name of provider
* __provider_format_logos__ - provider-format logos (such as Netflix Mail and Netflix Streaming)
	* __light__
	* __dark__
* __provider_format_id__ - provider-format's GoWatchIt ID
* __watch_now_url__ - provider URL to the movie via GoWatchIt  
* __category__ - avilabilitie's category such as dvd, online etc.

#### GET /api/v3/movies/:id/review
Returns a paginated list of all user reviews for a movie.

#### Fields
* __reviews__ - a collection of reviews each having
	* __user__ - name of the athor
	* __star_rating__ - number of starts the movie was given
	* __review__ - review's text

### POST /api/v3/movies/:id/review
Allows users to review movies. Requires the user to be logged-in.

#### Parameters
* __star_rating__ (required) - a user rating between 1 and 5
* __review__ (optional) - a text review



