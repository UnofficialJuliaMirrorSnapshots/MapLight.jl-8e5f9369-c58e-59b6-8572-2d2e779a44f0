# MapLight.jl

##### A Julia package targeting the MapLight API (v1)

## Quick start

```julia
julia> Pkg.add("MapLight")

julia> using MapLight

julia> my_auth = MapLight.authenticate("your_auth_key")
MapLight API Key (*****************************193)

julia> bill_search(my_auth, "us", "Electronic Communications Privacy Act Amendments Act of 2012")
["bills"=>{["session"=>"112","number"=>"2471","measure"=>"  H.R. 2471 (112<sup>th</sup>)\n","topic"=>"Electronic Communications Privacy Act Amendments Act of 2012","url"=>"http://maplight.org/us-congress/bill/112-hr-2471/1024048","prefix"=>"H","jurisdiction"=>"us"]}]

julia> bill_positions(my_auth, "us", 112, "H", 2471)
["bill"=>["url"=>"http://maplight.org/us-congress/bill/112-hr-2471/1024048","last_update"=>"2012-12-21T15:36:25Z","organizations"=>{["organization_id"=>"22489","name"=>"Center for Democracy & Technology","disposition"=>"support","citation"=>"Kravets, David (2011, September 23). Federal Law Blocks Netflix, Facebook Integration — But Should It?. <cite>Wired.com</cite>. Retrieved December 5, 2011, from <a href=\"http://www.wired.com/threatlevel/2011/09/netflix-video-privacy/\">http://www.wired.com/threatlevel/2011/09/netflix-video-privacy/</a>.","catcode"=>"J3000"],["organization_id"=>"25404","name"=>"Digital Media Association","disposition"=>"support","citation"=>"Gregory Alan Barnes, Director of Government Affairs, Digital Media Association (2011, October 13). <a href=\"http://www.digmedia.org/component/content/article/40/300-dima-applauds-members-of-the-house-judiciary-committee-for-streamlining-consent-requirements-under-the-video-privacy-protection-act\"><cite>DiMA Applauds Members of the House Judiciary Committee for Streamlining Consent Requirements under the Video Privacy Protection Act</cite></a>. Retrieved December 5, 2011, from Press Releases.","catcode"=>"C5140"],["organization_id"=>"22466","name"=>"Electronic Privacy Information Center","disposition"=>"oppose","citation"=>"Kravets, David (2011, September 23). Federal Law Blocks Netflix, Facebook Integration — But Should It?. <cite>Wired.com</cite>. Retrieved December 5, 2011, from <a href=\"http://www.wired.com/threatlevel/2011/09/netflix-video-privacy/\">http://www.wired.com/threatlevel/2011/09/netflix-video-privacy/</a>.","catcode"=>"J3000"],["organization_id"=>"27350","name"=>"Netflix","disposition"=>"support","citation"=>"Michael Drobac, director of Government Relations, Netflix (2011, September 22). <a href=\"http://blog.netflix.com/2011/09/help-us-bring-facebook-sharing-to.html\"><cite>Help us Bring Facebook Sharing to Netflix USA</cite></a>. Retrieved December 5, 2011, from The Netflix Blog.","catcode"=>"C5140"],["organization_id"=>"22694","name"=>"Facebook","disposition"=>"support","citation"=>"Carr, Austin (2011, August 22). Facebook, Netflix Push Congress on Social Integration, Video Privacy. <cite>Fast Company</cite>. Retrieved December 7, 2011, from <a href=\"http://www.fastcompany.com/1782164/facebook-netflix-push-congress-on-social-integration-video-privacy\">http://www.fastcompany.com/1782164/facebook-netflix-push-congress-on-social-integration-video-privacy</a>.","catcode"=>"C5140"],["organization_id"=>"22035","name"=>"American Civil Liberties Union","disposition"=>"oppose","citation"=>"Murphy, Laura W. (2012, January 31). <a href=\"http://www.aclu.org/files/assets/fnal_statement_hr_2471_013112_4.pdf\"><cite>Re: ACLU Opposes Expanded Unwarranted Law Enforcement Access to Private Rental Records and Broader Privacy Implications in HR 2471</cite></a>. Retrieved November 28, 2012, from ACLU.","catcode"=>"J7000"]}]]

julia> organization_search(my_auth, "Digital Media Association")
["organizations"=>{["organization_id"=>"25404","name"=>"Digital Media Association"]}]

julia> organization_positions(my_auth, "us", 25404)
["positions"=>{["number"=>"275","measure"=>"H.R. 275 (110<sup>th</sup>)","topic"=>"Global Online Freedom Act of 2007","last_update"=>"2011-08-29T20:44:13Z","disposition"=>"oppose","catcode"=>"C5140","prefix"=>"H","citation"=>" (n.d.). <a href=\"\"><cite>RE: H.R. 275, the “Global Online Freedom Act of 2007”</cite></a>. Retrieved n.d., from .","url"=>"http://maplight.org/us-congress/bill/110-hr-275/236522","session"=>"110","jurisdiction"=>"US"],["number"=>"2060","measure"=>"H.R. 2060 (110<sup>th</sup>)","topic"=>"Internet Radio Equality Act","last_update"=>"2011-08-29T20:28:47Z","disposition"=>"support","catcode"=>"C5140","prefix"=>"H","citation"=>" (n.d.). <a href=\"\"><cite>Congressmen Introduce Bill to Save Internet Radio</cite></a>. Retrieved n.d., from .","url"=>"http://maplight.org/us-congress/bill/110-hr-2060/291155","session"=>"110","jurisdiction"=>"US"],["number"=>"4279","measure"=>"H.R. 4279 (110<sup>th</sup>)","topic"=>"Prioritizing Resources and Organization for Intellectual Property Act of 2008","last_update"=>"2011-08-29T16:14:29Z","disposition"=>"support","catcode"=>"C5140","prefix"=>"H","citation"=>" (n.d.). <a href=\"\"><cite>Statement of Conyers</cite></a>. Retrieved n.d., from .","url"=>"http://maplight.org/us-congress/bill/110-hr-4279/377624","session"=>"110","jurisdiction"=>"US"],["number"=>"575","measure"=>"S. 575 (112<sup>th</sup>)","topic"=>"Debit Interchange Fee Study Act of 2011","last_update"=>"2012-12-20T21:51:15Z","disposition"=>"oppose","catcode"=>"C5140","prefix"=>"S","citation"=>"Undersigned Organizations (2011, June 6). <a href=\"https://www.wewear.org/assets/1/7/060611swipefee.pdf\"><cite>Dear Senator:</cite></a>. Retrieved August 6, 2012, from American Apparel and Footwear Association.","url"=>"http://maplight.org/us-congress/bill/112-s-575/900958","session"=>"112","jurisdiction"=>"US"],["number"=>"2471","measure"=>"H.R. 2471 (112<sup>th</sup>)","topic"=>"Electronic Communications Privacy Act Amendments Act of 2012","last_update"=>"2012-12-21T15:36:25Z","disposition"=>"support","catcode"=>"C5140","prefix"=>"H","citation"=>"Gregory Alan Barnes, Director of Government Affairs, Digital Media Association (2011, October 13). <a href=\"http://www.digmedia.org/component/content/article/40/300-dima-applauds-members-of-the-house-judiciary-committee-for-streamlining-consent-requirements-under-the-video-privacy-protection-act\"><cite>DiMA Applauds Members of the House Judiciary Committee for Streamlining Consent Requirements under the Video Privacy Protection Act</cite></a>. Retrieved December 5, 2011, from Press Releases.","url"=>"http://maplight.org/us-congress/bill/112-hr-2471/1024048","session"=>"112","jurisdiction"=>"US"],["number"=>"6480","measure"=>"H.R. 6480 (112<sup>th</sup>)","topic"=>"Internet Radio Fairness Act of 2012","last_update"=>"2012-12-21T01:16:16Z","disposition"=>"support","catcode"=>"C5140","prefix"=>"H","citation"=>"IRFC (n.d.). <a href=\"http://internetradiofairness.com/legislation/\"><cite>The IRFA: Good for Consumers, Artists and the Recording Industry</cite></a>. Retrieved November 20, 2012, from IRFC.","url"=>"http://maplight.org/us-congress/bill/112-hr-6480/1102695","session"=>"112","jurisdiction"=>"US"],["number"=>"3609","measure"=>"S. 3609 (112<sup>th</sup>)","topic"=>"Internet Radio Fairness Act of 2012","last_update"=>"2012-12-21T01:18:07Z","disposition"=>"support","catcode"=>"C5140","prefix"=>"S","citation"=>"IRFC (2012, October 25). Internet Radio Fairness Coalition Launches to Help Accelerate Growth and Innovation in Internet Radio To Benefit Artists, Consumers and the Recording Industry. <cite>MarketWatch: The Wall Street Journal</cite>. Retrieved November 1, 2012, from <a href=\"http://www.marketwatch.com/story/internet-radio-fairness-coalition-launches-to-help-accelerate-growth-and-innovation-in-internet-radio-to-benefit-artists-consumers-and-the-recording-industry-2012-10-25\">http://www.marketwatch.com/story/internet-radio-fairness-coalition-launches-to-help-accelerate-growth-and-innovation-in-internet-radio-to-benefit-artists-consumers-and-the-recording-industry-2012-10-25</a>.","url"=>"http://maplight.org/us-congress/bill/112-s-3609/1102959","session"=>"112","jurisdiction"=>"US"],["number"=>"3309","measure"=>"H.R. 3309 (113<sup>th</sup>)","topic"=>"Innovation Act","last_update"=>"2014-01-25T20:41:07Z","disposition"=>"support","catcode"=>"C5140","prefix"=>"H","citation"=>"undersigned organizations (n.d.). <a href=\"http://judiciary.house.gov/news/2013/12032013_PATENT/FINAL%20Growing%20Support%20for%20HR%20%203309.pdf\"><cite>Growing Support for H.R. 3309, &quot;The Innovation Act&quot;</cite></a>. Retrieved December 13, 2013, from House Committee on the Judiciary.","url"=>"http://maplight.org/us-congress/bill/113-hr-3309/2602316","session"=>"113","jurisdiction"=>"US"]}]
```


## API

### Bill Search

Returns an array of bills that match a particular string.

```julia
bill_search(auth::Auth, jurisdiction, search_str)

bill_search(auth::String, jurisdiction, search_str)

bill_search(jurisdiction, search_str; auth = authenticate())
```

- `auth`: An instance of `Auth` or an api key in the form of a string
- `jurisdiction`: Either `"us"` for federal or `"ca"` for california
- `search_str`: The string to search for (the full or partial name of a bill, for instance)


### Bill Positions

Returns an array of organization’s positions on a single bill.

```julia
bill_positions(auth::Auth, jurisdiction, session, prefix, number)

bill_positions(auth::String, jurisdiction, session, prefix, number)

bill_positions(jurisdiction, session, prefix, number; auth = authenticate())
```

- `auth`: An instance of `Auth` or an api key in the form of a string
- `jurisdiction`: Either `"us"` for federal or `"ca"` for California
- `session`: An integer
    * `109`: The 109th session of the United States Congress (2005-2006).
    * `110`: The 110th session of the United States Congress (2007-2008).
    * `111`: The 111th session of the United States Congress (2009-2010).
    * `112`: The 112th session of the United States Congress (2011-2012).
    * `2009`: The 2009-2010 session of the California Assembly.
    * `2011`: The 2011-2012 session of the California Assembly.
- `prefix`: A string
    * `"h"`: House Bill (i.e. H.R.)
    * `"hr"`: House Resolution (i.e. H.Res.)
    * `"hj"`: House Joint Resolution (i.e. H.J.Res.)
    * `"hc"`: House Concurrent Resolution (i.e. H.Con.Res.)
    * `"s"`: Senate Bill (i.e. S.)
    * `"sr"`: Senate Resolution (i.e. S.Res.)
    * `"sj"`: Senate Joint Resolution (i.e. S.J.Res.)
    * `"sc"`: Senate Concurrent Resolution (i.e. S.Con.Res.)
- `number`: The bill number (without the prefix)


## Bill List

Returns an array of organizations’ positions on all bills in a session. This response is cached and updated nightly.

```julia
bill_list(auth::Auth, jurisdiction, session; include_organizations = true, has_organizations = true)

bill_list(auth::String, jurisdiction, session; include_organizations = true, has_organizations = true)

bill_list(jurisdiction, session; auth = authenticate(), include_organizations = true, has_organizations = true)
```

- `auth`: An instance of `Auth` or an api key in the form of a string
- `jurisdiction`: Either `"us"` for federal or `"ca"` for California
- `session`: An integer
    * `109`: The 109th session of the United States Congress (2005-2006).
    * `110`: The 110th session of the United States Congress (2007-2008).
    * `111`: The 111th session of the United States Congress (2009-2010).
    * `112`: The 112th session of the United States Congress (2011-2012).
    * `2009`: The 2009-2010 session of the California Assembly.
    * `2011`: The 2011-2012 session of the California Assembly.
- `include_organizations`: `true` or `false` - whether to include the positions of organizations that took a stance
- `has_organizations`: `true` or `false` - whether to include in the response bills for which support and opposition are unknown


### Organization Search

Returns an array of organization IDs that match a particular string.

```julia
organization_search(auth::Auth, search_str, exact = false)

organization_search(auth::String, search_str, exact = false)

organization_search(search_str, exact = false; auth = authenticate())
```

- `auth`: An instance of `Auth` or an api key in the form of a string
- `search_str`: The string to search for (the full or partial name of an organization, for instance)
- `exact`: `true` or `false` - whether to search for an exact or partial string match


### Organization Positions

Returns an array an organization’s positions on bills.

```julia
organization_positions(auth::Auth, jurisdiction, org_id)

organization_positions(auth::String, jurisdiction, org_id)

organization_positions(jurisdiction, org_id; auth = authenticate())
```

- `auth`: An instance of `Auth` or an api key in the form of a string
- `jurisdiction`: Either `"us"` for federal or `"ca"` for california
- `org_id`: MAPLight.org’s internal identifier for organizations (output from the organization_search method)
