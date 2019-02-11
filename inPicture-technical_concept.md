# (Be) In Picture - technical concept

## Databases (servers)

There can be uncontrollable amount of independent databases around the world.

## API

Documented public `API` of database.

* versioning - `sem-ver`
* REST
* JSON response

## Data and links

* group / person
* impact
* citation
* event
* pointer

## Links

**@todo** The Key Feature - requires more work and public discussion.

### Examples

* person, group
	+ citation
		* said
	+ person
		* supperior
	+ group
		* owner
		* member
* event
* impact
	+ person
		* voted for
		* voted against
* citation
	+ citation
		* declines
		* verifies

## Sctucture
### Data tables

* nodes (data table)
* connections (data table)
* nodes__corrections
* connections__corrections
* votes
* vote_polls
* sources
* source media
* places

#### M:N

+ source:ALL_DATA_TABLES

#### Nodes

| _UUID_ **[PK]** | _bytemark_ (8bytes) | date_start Date() | date_end Date(NULL) | updated Date() | author_UUID **[FK]**? | name char(60) | text char(160) | picture char(2048) | type set() | pointed_fingers SUM(pointers where FK=this.PK) | place_UUID |
|---|---|---|---|---|---|---|---|---|---|---|---|
| inPicture-type-2378ghj543 | 0000000 |

#### Connections

| _UUID_ | _bytemark_ (8bytes) | date_start | date_end Date(NULL) | date (last update) | author | type set() | left_item_UUID | right_item_UUID | name Char(60) |
|---|---|---|---|---|---|---|---|---|---|
| inPicture-con-type-2378ghj543 | 0000000 |

#### Votes

* vote = TRUE -> means Yes

| ID | author_UUID **[FK]** | item_UUID | vote Boolean(NULL) | locked Boolean(FALSE) |
|---|---|---|---|---|

#### Votes_public
| ID | author_UUID **[FK]** | picture_UUID | vote Boolean(NULL) |
|---|---|---|---|---|

#### Vote polls

* Polls which are created by logic in app automatically - have NULL author. E.q. annual board vote.

| UUID | name | date_start | date_end | author (can be NULL) | item_UUID (can be NULL) | locked Boolean(FALSE) |
|---|---|---|---|---|---|---|

#### Sources

| ID | url | sources-media_UUID (can be NULL) |
|---|---|---|

#### Source media

Smart layer to help with qualification of sources for redactors decisions. Based on REGEXP's from URL.

| _UUID_ **[PK]** | _bytemark_ (8bytes) | regexp Char(256) | updated Date() | author_UUID **[FK]**? | name char(60) | type set(journal, gov, ...) |
|---|---|---|---|---|---|---|---|---|---|
| inPicture-media-2378ghj543 | 0000000 |

#### Users (author/redactor)
| _UUID_ **[PK]** | username | auth_token (? - PGP key ? [^authMethod]) | 
|---|---|---|---|---|---|---|---|---|---|

#### Pictures
| _UUID_ **[PK]** | author_UUID | name | votes_up | votes_down | updated |
|---|---|---|---|---|---|---|---|---|---|


#### Tags

Voters for tag relevancy are redactors.
Categories should be objective, such as: "Foreign policy", "Finances", ...

| _UUID_ **[PK]** | author_UUID | name | votes_up | votes_down | updated | icon | is_category |
|---|---|---|---|---|---|---|---|---|---|

#### Pointers

One of few tables, that have impact from normal users.

Relevancy of pointers ("Point your finger") is based on amount of users who used same one for same item.

*@todo* decide how many fingers pointing to something is needed to make them publicly visible.

| _UUID_ **[PK]** | user_UUID | tag_UUID | item_UUID |
|---|---|---|---|---|---|---|---|---|---|

#### Places

| _UUID_ **[PK]** | author_UUID | name |
|---|---|---|---|---|---|---|---|---|---|

## Bytemark of main data tables

Bytemark INT value is used as information weight and is updated based on voting of redactors.

* affected tables -> optimized for order by bytemark (for performance)

| _value_/_byte_ | _1._ | _2._ | _3._ | _4._ | _5._ | _6._ | _7._ | _8._ |
|---|---|---|---|---|---|---|---|---|
| **0 _FALSE_** |archived||not approved| --- |potentionaly misleading or incomplete|||denied|unlocked
| **1 _TRUE_** |active| _verified_ = approved by 2/3 of redactors and more then one| _approved_ by one redactor and >= 1/2 of redactors| _fact_ = considered as objective fact by 2/3 redactors and > 1| _objective_ = considered as objective by 1/2 redactors and >= 1| _serious_ considered significant 2/3 of redactors and more then one| _impactful_ = considered significant 1/2 of redactors >= 1|not denied|locked







## Databases.list

Publicly accessible list of existing databases.

```JSON
[
	{
		lang: 'en_US',
		url: 'inPicture:API_ROOT_URL',
		name: '(Be) In Picture',
		icon: 'data:=38706hjbvk4hg35g32343...'
	},
	{
		lang: 'cs_CZ',
		url: 'inPicture:vObraze.cz.gov',
		name: {
			cs_CZ: 'Buď v Obraze!',
			en_US: 'Czech In Picture!'
		},
		icon: 'data:=/ik,;aeulmrszhdwejlk213kj4b;k66p;45hv...'
	},
	{
		lang: 'en_US',
		url: 'inPicture:inPicture.thepiratebay.org/globalWorldNews',
		name: 'Stay in picture of todays IT world @by Pirates of Caribbean'
	},
	{
		lang: 'en_US',
		url: 'inPicture:illuminate.com/bigConspiracy:42',
		name: 'Juicy conspiracy of everything - everything is connected! Open your eyes!'
	}
	
	/* ... */
	
]
```

Other data load through API. (Like description, rules, information about owner.)

## Authentication

To be picked.
Possibilities are:

* OpenID
* register simple account with PGP authentication token
* other? ...


## Future possibilities

### Machine-learning

* Independent neuron networks to create `pictures` and `pointers` and suggest `connections`.


[^authMethod]: Authentication method [](#authentication)
