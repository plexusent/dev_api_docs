
### GET theatrical endpoints

Returns theatrical showtimes in JSON format

* api/v3/movies/:id/showtimes
* api/v3/movies/:id/theaters
* api/v3/movies/:id/theaters/:theater_id/showtimes

### GET api/v3/movies/:id/showtimes.json

Required parameters - movie_id

Optional query parameters - zipcode - Zipcode is required for supplying the data, but will be calculated based on user's IP address, if not supplied through query parameter.

Returns 5 theaters closest to zipcode center, that are currently showing the movie requested, and requested movie showtimes.

__Fields__

* __showtimes__
 * __zipcode__ - calculated or supplied zipcode
 * __id__ - movie id
 * __title__ - movie title
 * __theaters__ - array of 5 closest theaters.
  		* __name__ - theater name
  		* __id__ - theater id
  		* __address__ - theater address
  		* __city__ - theater city
  		* __distance__ distance from zipcode center
  		* __showtimes__ - array of showtimes for requested movie
  		* __purchase url__ - ticket purchase url    


### GET api/v3/movies/:id/theaters.json

Required parameters - movie_id

Optional query parameters - zipcode - Zipcode is required for supplying the data, but will be calculated based on user's IP address, if not supplied through query parameter.

Optional query parameters - page and per_page

Returns a paginated array of all theaters in zipcode proximity currently showing the movie requested, and requested movie showtimes.

__Fields__

* __theaters__ 
 * __zipcode__ - calculated or supplied zipcode
 * __id__ - movie id
 * __title__ - movie title
 * __theaters__ - array of all theaters showing movie
 		* __name__ - theater name
 		* __id__ - theater id
 		* __address__ - theater address
 		* __city__ - theater city
 		* __distance__ distance from zipcode center
 		* __showtimes__ - array of showtimes for requested movie  
  		* __purchase url__ - ticket purchase url    


### GET api/v3/movies/:id/theaters/:theater_id/showtimes.json

Required parameters - movie_id and theater_id

Returns theater data and showtimes for the requested movie/theater combination

__Fields__

* __showtimes__
	* __movie__ - movie name
	* __id__ - movie id
	* __theater name__ 
	* __theater id__
	* __theater address__
	* __showtimes__ - array of showtimes for requested movie
