### GET search endpoints

Returns matches of a term or criteria for movie, show, and contribution (director/cast) items.
These can be used for search features as well as AJAX autocomplete functionality.

* api/v3/search.json
* api/v3/search/movies.json
* api/v3/search/shows.json
* api/v3/search/contributors.json

__Note:__ Since the GoWatchIt database includes both movie AND television data, we will
refer to individual items as 'watchables'. Watchables currently include
movies and TV shows.

### GET api/v3/search

General search enpoint. Response will include top 5 results in each of the
following categories: movies, shows and contributors.

#### General parameters

   - *term* - a set of keywords such as a watchable title, actor's name etc.
   - *genres* - watchable genres such as 'comedy', 'horror' etc. Search
   results will include watchables in the specified genres.
   
   ```
   genres[]=comedy
   ```
   
   - *year* - a watchable's release year
   - *pg_ratings* - parental guidelines ratings. Search results will
   include watchables in the specified ratings. Accepted movie ratings: *G,
   PG, PG-13, R, NC-17* (MPAA <http://www.mpaa.org/film-ratings>). Accepted
   TV ratings: *TV-Y, TV-Y7, TV-G, TV-PG, TV-14, TV-MA* (TV parental
   guidelines <http://en.wikipedia.org/wiki/TV_Parental_Guidelines>)
   
   ```   
   pg_ratings[]=pg-13
   ```
   - *run_time_min* - a watchable's minimum duration
   - *run_time_max* - a watchable's maximum duration

#### Availability parameters

Allow customization of search results based on a watchable's current availability.

   - *provider_format_ids* - includes watchables in the specified GoWatchIt provider formats. For example,
   
   ```
   provider_format_ids[]=1
   ```
   
   will only include watchables available via Netflix Mail unless other availability parameters are specified.
   - *categories* - a list of availability categories. Search results will only include watchables available in the specified categories. 

   Valid values: 
      * *presale* (presale theater tickets are available)
      * *theater* (currently played in theaters) 
      * *online* (available for online streaming) and
      * *dvd* (available on DVD/Blu-Ray). For example, a search specifying
   ```
   categories[]=online
   ```
   will only include watchables available for streaming

#### Sorting
If a search term is supplied, the watchables will always be sorted by relevance. Otherwise, the watchables will be sorted by title in the ascending order. 


**Note on formatting collection URL parameters:**

__[ ]__ denotes parameters that can accept a collection of values. For
example, in order to retrieve watchables that are available for streaming
OR on dvd OR both, pass the *categories* like so

   ```
   categories[]=online&categories[]=dvd
   ```

The same pattern applies to all collection parameters such as
*provider_format_ids*, *genres*,*pg_ratings* etc.

### GET api/v3/search/movies

Supports all general search filters (year, genres, categories etc.) but works only with movies.

Additionally, 

1. Term-less search queries' default sort order can be overriden by following parameters. 
   * *sort* - attribute by which the returned watchables will be sorted. Currently supported: title, year
   * *sort_order* - the order in which search results will be sorted. Valid values: asc, desc

   ```
   http://gowatchit.com/api/v3/search/movies?genres[]=comedy&sort=year&sort_order=desc
   ```

2. Maximum number of search results can be limited by *num_items*

   ```
   http://gowatchit.com/api/v3/search/movies?genres[]=comedy&num_items=100
   ```
3. Search results can be paginated by specifying *offset* 

   ```
   http://gowatchit.com/api/v3/search/movies?genres[]=comedy&num_items=100&offset=20
   ```
   
### GET api/v3/search/shows

Search TV shows. If no filtering options are specified, the endpoint will return all the known shows (paginated) sorted in the alphabetical order.

#### Supported filters

* *term* - a set of keywords to match against show titles. Only the titles matching the term will be returned.

* *genres* - only the shows matching the specified genres will be returned.

   ```
   http://mpaa.staging-gowatchit.com/api/v3/search/shows?genres[]=action
   ```
* *pg_ratings* - only the shows with the specified [parental guidelines ratings](http://www.tvguidelines.org/ratings.htm) will be returned
   
   ``` 
   http://mpaa.staging-gowatchit.com/api/v3/search/shows?pg_ratings[]=tv14
   ```

* *year* - only the shows premiered in the specified year will be returned

   ```
   http://mpaa.staging-gowatchit.com/api/v3/search/shows?year=2014
   ```
* *categories* - a list of availability categories. (supported: presale, theater, dvd, online). Only watchables available in the specified categories will be returned.

   ```
   http://mpaa.staging-gowatchit.com/api/v3/search/shows?categories[]=online
   ```

   All of the above filters can be combined.
   
#### Sorting

Term-less search queries' default sort order can be overriden by following parameters. 
   * *sort* - attribute by which the returned watchables will be sorted. Currently supported: title, year
   * *sort_order* - the order in which search results will be sorted. Valid values: asc, desc


### GET api/v3/search/contributors

Returns a list of contributors such as cast members, directors, writers etc. matched to supplied *term*.
   ```
   http://gowatchit.com/api/v3/search/contributors?term=allen
   ```
   

   

  

