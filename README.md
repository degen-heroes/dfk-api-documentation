# Unofficial DFK API Documentation

This documentation refers to the REST API of DeFi Kingdoms. It has not been officially released for public use, but it has been more than a few months since its release and no other viable alternative to a REST API exists.

DFK Developers discourage the use of the API due to possible breaking changes. This documentation will attempt to stay up to date with all modifications.

## REST URL

The URL of the REST API is as follows:

```
https://us-central1-defi-kingdoms-api.cloudfunctions.net/
```

All calls to the API need to prepend this url.

## API Parameters

All API requests are using POST to and pass along pagination and filtering parameters:

* **offset** `{number}`: Pagination offset, start with `0`.
* **limit** `{number}`: Pagination limit of records, default is `9999`.
* **order** `{Object}`: Shorting of records.
    * **orderBy** `{string}`: Attribute to sort by:
    * **orderDir** `{enum}`: Sorting direction, can be `asc` or `desc`.
* **params** `{Array<Object>}`: Query parameters to filter records with:
    * **field** `{string}` Property to filter for.
    * **operator** `{enum}` Comparison operator, can be one of: `=`, `>=`, `<=`, `in`.
    * **value** `{*}` The expected value to filter by.


## Heroes

Query for heroes and sales of heroes.

* POST `/query_heroes`

### Querying Examples for Heroes


<details>
  <summary><span style="font-size: 1.5em;">Query for heroes of a specific wallet:</span></summary>
<br />

```json
{
    "limit":9999,
    "offset":0,
    "order": {
        "orderBy":"id",
        "orderDir":"asc"
    },
    "params": [{
        "field":"owner",
        "operator":"=",
        "value":"0x67221b267cee49427bAa0974ceac988682192977"
    }]
}
```
</details>
<details>
  <summary><span style="font-size: 1.5em;">Query for heroes on sale:</span></summary>
<br />

```json
{
    "limit":100,
    "offset":0,
    "order": {
        "orderBy":"salesprice",
        "orderDir":"asc"
    },
    "params": [{
        "field":"salesprice",
        "operator":">=",
        "value":1000000000000000000
    }]
}
```
</details>
<details>
  <summary><span style="font-size: 1.5em;">Query for heroes on private sale:</span></summary>
<br />

```json
{
    "limit":100,
    "offset":0,
    "order": {
        "orderBy":"salesprice",
        "orderDir":"asc"
    },
    "params": [{
        "field":"privateauctionprofile",
        "operator":">=",
        "value":"0x67221b267cee49427bAa0974ceac988682192977"
    }]
}
```
</details>

### Result Sample of Heroes


<details>
  <summary><span style="font-size: 1.5em;">Result Sample of Heroes:</span></summary>
<br />
```json
[
    {
        "id": "502",
        "numberid": "502",
        "owner": "0xCb67fEFFA39792fe2769796b2407d851faAff9ca",
        "creator": null,
        "statgenes": "281364166417808041148923757084678628457663213035028620104753236490527050",
        "visualgenes": "60557421229657533075248750082607857616771902340872764390829249274249350",
        "rarity": 2,
        "shiny": true,
        "generation": 0,
        "firstname": 1867,
        "lastname": 1711,
        "shinystyle": 5,
        "mainclass": "6",
        "subclass": "2",
        "summonedtime": "1633046465",
        "nextsummontime": "1646991108",
        "summonerid": "0",
        "assistantid": "0",
        "summons": 42,
        "maxsummons": 11,
        "staminafullat": "1646703502",
        "hpfullat": "0",
        "mpfullat": "0",
        "level": 5,
        "xp": "644",
        "currentquest": "0x0000000000000000000000000000000000000000",
        "sp": 0,
        "status": "0",
        "strength": 14,
        "intelligence": 10,
        "wisdom": 14,
        "luck": 13,
        "agility": 9,
        "vitality": 14,
        "endurance": 13,
        "dexterity": 10,
        "hp": 281,
        "mp": 57,
        "stamina": 27,
        "strengthgrowthp": 6000,
        "intelligencegrowthp": 2500,
        "wisdomgrowthp": 5000,
        "luckgrowthp": 3000,
        "agilitygrowthp": 6000,
        "vitalitygrowthp": 6000,
        "endurancegrowthp": 5700,
        "dexteritygrowthp": 6000,
        "strengthgrowths": 1375,
        "intelligencegrowths": 625,
        "wisdomgrowths": 875,
        "luckgrowths": 1625,
        "agilitygrowths": 1750,
        "vitalitygrowths": 1250,
        "endurancegrowths": 1525,
        "dexteritygrowths": 1375,
        "hpsmgrowth": 2500,
        "hprggrowth": 3500,
        "hplggrowth": 4000,
        "mpsmgrowth": 3000,
        "mprggrowth": 4000,
        "mplggrowth": 3000,
        "mining": 55,
        "gardening": 77,
        "foraging": 35,
        "fishing": 22,
        "profession": "gardening",
        "passive1": "Basic2",
        "passive2": "Basic2",
        "active1": "Basic6",
        "active2": "Basic2",
        "statboost1": "LCK",
        "statboost2": "END",
        "statsunknown1": "5",
        "element": "light",
        "statsunknown2": "0",
        "gender": "female",
        "headappendage": "6",
        "backappendage": "4",
        "background": "arctic",
        "hairstyle": "4",
        "haircolor": "578761",
        "visualunknown1": "0",
        "eyecolor": "896693",
        "skincolor": "aa5c38",
        "appendagecolor": "2a386d",
        "backappendagecolor": "2a386d",
        "visualunknown2": "6",
        "assistingauction": null,
        "assistingprice": null,
        "saleauction": "941550",
        "saleprice": "5800000000000000000000",
        "privateauctionprofile": null,
        "summoner_id": null,
        "summoner_mainclass": null,
        "summoner_rarity": null,
        "summoner_generation": null,
        "summoner_visualgenes": null,
        "assistant_id": null,
        "assistant_mainclass": null,
        "assistant_rarity": null,
        "assistant_generation": null,
        "assistant_visualgenes": null,
        "owner_name": "FoLu",
        "owner_picid": null,
        "owner_address": "0xCb67fEFFA39792fe2769796b2407d851faAff9ca",
        "owner_nftid": "3",
        "owner_collectionid": "0",
        "assistauction_startingprice": null,
        "assistauction_endingprice": null,
        "assistauction_duration": null,
        "assistauction_startedat": null,
        "saleauction_startingprice": "5800000000000000000000",
        "saleauction_endingprice": "5800000000000000000000",
        "saleauction_duration": "60",
        "saleauction_startedat": "1646732218",
        "firstname_string": "Cullodena",
        "lastname_string": "Thunmutul",
        "summons_remaining": 11,
        "current_stamina": "27"
    }
]
```
</details>

## Heroes Renting

* POST `/query_assistauctions`

### Querying Examples for Renting Heroes


<details>
  <summary><span style="font-size: 1.5em;">Query for past rents:</span></summary>
<br />

```json
{
    "limit":100,
    "offset":0,
    "order": {
        "orderBy":"endedat",
        "orderDir":"desc"
    },
    "params": [{
        "field":"open",
        "operator":"=",
        "value":false
    }]
}
```
</details>

### Result Sample of Renting Heroes

<details>
  <summary><span style="font-size: 1.5em;">Result Sample of Renting Heroes:</span></summary>
<br />

```json
[
    {
        "id": "167163",
        "seller": "0x043C91573014f46f58F73dDfaB865a2536532E81",
        "tokenid": "135528",
        "startingprice": "23000000000000000000",
        "endingprice": "23000000000000000000",
        "duration": "60",
        "startedat": "1646729497",
        "winner": "0xf4d3aE202c9Ae516f7eb1DB5afF19Bf699A5E355",
        "endedat": "1646744741",
        "open": false,
        "purchaseprice": "23000000000000000000",
        "hero_id": "135528",
        "hero_mainclass": "7",
        "hero_rarity": 4,
        "hero_shiny": false,
        "seller_name": "DonCrypto",
        "seller_picid": null,
        "seller_nftid": "7",
        "seller_collectionid": "0",
        "seller_address": "0x043C91573014f46f58F73dDfaB865a2536532E81",
        "winner_name": null,
        "winner_picid": null,
        "winner_nftid": null,
        "winner_collectionid": null,
        "winner_address": null
    }
]
```
</details>
