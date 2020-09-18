NHL API Interface Development Reflection
================

This is a reflection regarding a [recently completed
vignette](https://fd54386.github.io/NHL-API-Interface) to write a few
hooks into two NHL APIs. For these APIs there is no official
documentation, just limited community documentation available through
other
[blogs](https://www.kevinsidwar.com/iot/2017/7/1/the-undocumented-nhl-stats-api)
and [gitlab](https://gitlab.com/dword4/nhlapi/-/tree/master) pages.
Functions to pull from several endpoints were created as an academic
assignment, along with an exploratory analysis of the data available to
evaluate Wayne Gretzky’s credentials. Turns out that guy has a lot of
goals and assists, but not many people named after him.

This was an awkward function set and analysis to pull together in the
context of the academic assignment. The functions needed to be able to
pull for both a common name and TeamID, however the team and
franchiseIDs are not equivalent and swap out between tables. My initial approach was to use one
helper function that built the entire modifier – it should have been
simple enough, but I quickly ran into the issue of field names changing
across endpoints. I wound up needing modifiers that were endpoint
specific, and so the scope of the helper function and it’s interaction
with the rest had to be completely redesigned after an initial version
had already been implemented.

Ultimately, the assignment wound up being a lot of work for a very
limited range of modifiers. It shaped the analysis, as well – working
with actual player stats by season (from the stats API) instead of
career min and maxes would allow much more accurate correlations. That
data exists across another dozen or so endpoints on each API that would
need to be implemented for a finished product. The current functionality
will at least save time on validating the endpoint URLs (letter case has
tripped me up several times). That being said, it’s not clear how well
this design will scale to accommodating all of the Stats API endpoints.
The `/people` endpoint for example has about a dozen different stats
calls that would be hard to memorize– with my current implementation a
user would have to look up the vignette documentation for specific
endpoints. This seems equivalent to looking up the community
documentation as needed, for little gain.

For future projects, there are a few takeaways. First, always explore
the available endpoints before implementing anything, and identify how
well the keys match up. This will affect the design of any functions and
ability to reuse code. Second, focus on solutions that don’t need a lot
of memorization from the end-user. I think the empty `pullNHLAPI()`
evaluation is a starting example of this, providing printouts of all of
the different options when none were specified. A better solution might
be to do some interactive console work that helps inform and build
conditions as the user goes along, answering questions about available
endpoints, their modifiers, and fields to filter on.
