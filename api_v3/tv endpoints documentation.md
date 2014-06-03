# TV endpoints documentation.

### GET TV endpoints

Returns TV data in JSON format 

* api/v3/shows
* api/v3/shows/:id
* api/v3/shows/:id/availabilites
* api/v3/shows/:id/lite
* api/v3/seasons/:id
* api/v3/seasons/:id/availabilites
* api/v3/episodes/:id

**Note About TV Availabilities**

Our television data is hierarchical in nature, with `Shows` having `Seasons` which have `Episodes`.
In rare cases, Shows may directly possess episodes, but typically they will belong to a season.

Each of the three levels may have their own availability records. For example, most availabitities are on the 
episode level, however iTunes has full "Season Passes" available for a one-time purchase. It's possible but not common
for a Show to have an availability.

Episode availabilities are __not__ considered availabilities of their parent show or season's API endpoint. 
(If this were the case, The Simpsons "show" endpoint would contain 525+ episodes).

To retrieve a Show's list of episodes, the client must first query `api/v3/shows/:id`, then read the available season ids shown. 
Next, the client should query `api/v3/seasons/:id` and retrieve the episode ids listed. 
Finally, the client may query specific episodes by id at `api/v3/episodes/:id`

These endpoints below have a special properties of direct and related availabilities:
 * `/api/v3/shows/:id`
 * `/api/v3/shows/:id/availabilities`
 * `/api/v3/seasons/:id`
 * `/api/v3/seasons/:id/availabilites`

A direct availabilities is, as described above, directly for that show or season.
A related availability is the lastest episode of the latest season. This is only shown when one is available.
The presence of any current direct or related availabilty will cause the `available` attribute to be true.

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

### GET api/v3/shows/:id

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
	   		* __online__
	   		* __dvd__ - all of these categories if present consist of:
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

See "Note About TV Availabilities" at the top of this document for more information about availabilities.

### GET api/v3/shows/:id/availabilities.json

Required parameter - show_id

Returns availabilities for specific show

__Fields__


* __availabilities__
	 * __direct__
	 * __related__ - both direct and related if present consist of:
	 	* __presale__
	 	* __theater__
	 	* __online__ 
	 	* __dvd__ - all of these categories if present consist of:
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

See "Note About TV Availabilities" at the top of this document for more information about availabilities.

### GET api/v3/shows/:id/lite.json

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

### GET api/v3/seasons/:id.json

Required parameter - season_id

Returns a season metadata, array of season episodes, and direct and related season availabilities

__Fields__

* __season__
 * __id__ - season id
 * __title__ - season title
 * __description__ - short synopsis of season
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
	 	 	* __theater__
	 	 	* __online__
	 	 	* __dvd__
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

See "Note About TV Availabilities" at the top of this document for more information about availabilities.

### GET api/v3/seasons/:id/availabilites.json

Required parameters - season_id

Returns direct and related season availabilities

__Fields__

* __availabilities__
 	* __direct__
 	* __related__
 	 	* __presale__
 	 	* __theater__
 	 	* __online__
	 	* __dvd__
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
	 
See "Note About TV Availabilities" at the top of this document for more information about availabilities.

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
	 	* __presale__
	 	* __theater__
	 	* __online__
	 	* __dvd__
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
	 * __related__ - always null for episodes
* __available__ - true/false
