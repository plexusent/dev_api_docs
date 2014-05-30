# TV endpoints documentation.

### GET TV endpoints

Returns TV data in JSON format 

* api/v3/shows
* api/v3/shows/:id
* api/v3/shows/:id/availabilites
* api/v3/shows/:id/lite
* api/v3/seasons
* api/v3/seasons/:id
* api/v3/seasons/:id/availabilites
* api/v3/episodes/:id

### GET api/v3/shows.json
Returns a paginated array of all shows in database.


Optional query parameters - page and per_page

__Fields__
	
* __shows__ - represents array of all shows 
					

a single show consist of

 * __id__ - show id
 * __title__ - show title
 * __description__ - short synopsis of show
 * __poster file name__ 
 * __year__ - release year
 * __network__ - broadcast network
 * __pg rating id__ - parental guidelines id
 * __language__ 
 * __trailer url__
 * __genre__ - watchable genres such as 'comedy', 'horror' etc.
 * __contributors__

### GET api/v3/show/:id

Required parameter - show_id
 
Returns show metadata, array of seasons and direct and related availabilities for the show

__Fields__

* __show__
 * __id__ - show id
 * __title__ - show title
 * __year__ - release year
 * __description__ - short synopsis of show
 * __genre__ - watchable genres such as 'comedy', 'horror' etc.
 * __pg rating__ - parental guidelines id
 * __premiere__ - date of premiere
 * __contributors__
 * __poster url__ 
 * __trailer url__
 * __language__ 
 * __seasons__ - array, each element consists of:  
  		* __id__ - season id
  		* __number__ - season number
  		* __title__ - season title
 * __availabilities__ - represent direct and/or related availabilities for the show
  		* __direct__
  		* __related__ - both direct and related if present consist of:
	   		* __presale__
	   		* __theater__
	   		* __onlines__
	   		* __dvds__ - all of these categories if present consist of:
	   			* __format line__
	    		* __buy line__
	    		* __rent line__
	    		* __provider name__
	    		* __provider logos__
	     			* __light__
	     			* __dark__
	    		* __watch now url__
	    		* __direct url__
	    		* __provider format id__
	    		* __category__
 * __available__ - returns true if there are availabilities for the show, false if there aren't any

### GET api/v3/show/:id/availabilities.json

Required parameter - show_id

Returns availabilities for specific show

__Fields__


* __availabilities__
	 * __direct__
	 * __related__ - both direct and related if present consist of:
	 	* __presale__
	 	* __theaters__
	 	* __online__ 
	 	* __dvds__ - all of these categories if present consist of:
		 	* __format line__
		 	* __buy line__
		 	* __rent line__
		 	* __provider name__
		 	* __provider logos__
		 		* __light__
		 		* __dark__
		 	* __watch now url__
		 	* __direct url__
		 	* __provider format id__
		 	* __category__
* __available__ - returns true if there are availabilities for the show, false if there aren't any

### GET api/v3/show/:id/lite.json

Required parameter - show_id

Optional parameters - providers(=true or false) - default true, if set to false doesn't return provider data
 
Returns lightweight show metadata and available provider's ids and logos

__Fields__  

* __show__
 * __id__ - show id
 * __title__ - show title
 * __year__ - release year
 * __description__ - short synopsis of show
 * __genre__ - watchable genres such as 'comedy', 'horror' etc.
 * __pg rating__ - parental guidelines id
 * __premiere__ - date of premiere
 * __poster url__
 * __trailer url__
 * __language__
 * __providers__ - consist of:
 		* __1__ - provider id
 			* __light logo__ - provider logo light
 			* __dark logo__ - provider logo dark
 * __available__ - returns true if there are availabilities for the show, false if there aren't any    

### GET api/v3/seasons.json

Returns a paginated array of all shows in database.

Optional query parameters - page and per_page

__Fields__

* __shows__ - array of all shows consist of
 * __id__ - show id
 * __title__ - show title
 * __description__ - short synopsis of show
 * __poster file name__ 
 * __year__ - release year
 * __network__
 * __pg rating id__ - parental guidelines id
 * __language__ 
 * __trailer url__
 * __genre__ - watchable genres such as 'comedy', 'horror' etc.
 * __contributors__

### GET api/v3/seasons/:id.json

Required parameter - season_id

Returns a season metadata, array of season episodes, and direct and related season availabilities

__Fields__

* __season__
 * __id__ - season id
 * __title__ - season title
 * __premiere__ - season premiere date
 * __contributors__
 * __season number__
 * __poster url__
 * __show id__
 * __episodes__ - array of episodes, each consists of:
	 * __id__ - episode id
	 * __number__ season episode number
	 * __title__ episode title
 * __availabilities__ - direct and related season availabilities
	 	* __direct__
	 	* __related__
	 	 * __presale__
	 	 * __theaters__
	 	 * __onlines__
	 	 * __dvds__
			 * __format line__
			 		* __buy line__
			 		* __rent line__
			 		* __provider name__
			 		* __provider logos__
			 			* __light__
			 			* __dark__
			 		* __watch now url__
			 		* __direct url__
			 		* __provider format id__
			 		* __category__
	* __available__ - true or false

### GET api/v3/seasons/:id/availabilites.json

Required parameters - season_id

Returns direct and related season availabilities

__Fields__

* __availabilities__
 	* __direct__
 	* __related__
 	 * __presale__
 	 * __theaters__
 	 * __onlines__
	 * __dvds__
	 		* __format line__
		 	* __buy line__
		 	* __rent line__
		 	* __provider name__
		 	* __provider logos__
		 		* __light__
		 		* __dark__
		 	* __watch now url__
		 	* __direct url__
		 	* __provider format id__
		 	* __category__
	* __available__
	 
### GET api/v3/episodes/:id.json

Required parameters - episode_id

Returns episode metadata, and availabilities

__Fields__

* __id__ - episode id
* __title__ - episode title
* __description__ - short synopsis of episode
* __premiere__ - episode premiere date
* __episode number__ - episode number in season
* __image url__
* __air date time__
* __contributors__
* __show id__
* __season id__
* __availabilities__
	 * __direct__
	 * __related__
	 	* __presale__
	 	* __theaters__
	 	* __onlines__
	 	* __dvds__
		   * __format line__
		   * __buy line__
		   * __rent line__
		   * __provider name__
		   * __provider logos__
		     * __light__
		     * __dark__  
		   * __watch now url__
		   * __direct url__
		   * __provider format id__
		   * __category__   
	* __available__ - true/false
