# account
## AccountStatus
accessMask = 33554432

## APIKeyInfo

## Characters

# api
## CallList

# char
******

## AccountBalance
``/char/AccountBalance.xml.aspx``  

* __Access mask:__ 1

## AssetList
``/char/AssetList.xml.aspx``

* __Access mask:__ 2
* __Paramaters:__
    * __flat:__ bool (0/1)

## Blueprints
``/char/Blueprints.xml.aspx``

* __Access mask:__ 2

Data:
<table border="1">
    <tbody>
        <tr>
            <td>blueprints</td>
            <td><strong>rowset</strong></td>
            <td></td>
            <td>Rowset containing 1 row per blueprint.</td>
        </tr>
        <tr>
            <td></td>
            <td>itemID</td>
            <td><strong>long</strong></td>
            <td>The actual item ID.</td>
        </tr>
        <tr>
            <td></td>
            <td>locationID</td>
            <td><strong>long</strong></td>
            <td>The location ID of where  the blueprint is located.</td>
        </tr>
        <tr>
            <td></td>
            <td>typeID</td>
            <td><strong>int</strong></td>
            <td>Type ID of the blueprint.</td>
        </tr>
        <tr>
            <td></td>
            <td>typeName</td>
            <td><strong>int</strong></td>
            <td>English name for the type of blueprint.</td>
        </tr>
        <tr>
            <td></td>
            <td>flagID</td>
            <td><strong>int</strong></td>
            <td>Flag for where the item is located.</td>
        </tr>
        <tr>
            <td></td>
            <td>quantity</td>
            <td><strong>int</strong></td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td>timeEfficiency</td>
            <td><strong>int</strong></td>
            <td>The TE level of the blueprint.</td>
        </tr>
        <tr>
            <td></td>
            <td>materialEfficiency</td>
            <td><strong>int</strong></td>
            <td>The ME level of the blueprint.</td>
        </tr>
        <tr>
            <td></td>
            <td>runs</td>
            <td><strong>int</strong></td>
            <td>The number of remaining runs for the blueprint. -1 for BPO.</td>
        </tr>
    </tbody>
</table>

|            |                    |          |                                                             |
|------------|--------------------|----------|-------------------------------------------------------------|
| blueprints | __rowset__         |          | Rowset containing 1 row per blueprint.                      |
|            | itemID             | __long__ | The actual item ID.                                         |
|            | locationID         | __long__ | The location ID of where  the blueprint is located.         |
|            | typeID             | __int__  | Type ID of the blueprint.                                   |
|            | typeName           | __int__  | English name for the type of blueprint.                     |
|            | flagID             | __int__  | Flag for where the item is located.                         |
|            | quantity           | __int__  |                                                             |
|            | timeEfficiency     | __int__  | The TE level of the blueprint.                              |
|            | materialEfficiency | __int__  | The ME level of the blueprint.                              |
|            | runs               | __int__  | The number of remaining runs for the blueprint. -1 for BPO. |

Eample response: (this is test data, need to have a think about inlcuding cachedUntil for example data)
```xml
<result>
    <rowset name="blueprints" key="itemID" columns="itemID,locationID,typeID,typeName,flagID,quantity,timeEfficiency,materialEfficiency,runs">
        <row itemID="1000000029372" locationID="60014929" typeID="11568" typeName="Avatar Blueprint" flagID="4" quantity="497" timeEfficiency="0" materialEfficiency="0" runs="-1"/>
        <row itemID="1000000029377" locationID="60014929" typeID="33876" typeName="Prophecy Blood Raiders Edition Blueprint" flagID="4" quantity="-2" timeEfficiency="0" materialEfficiency="0" runs="20000"/>
    </rowset>
</result>
```

## CalendarEventAttendees
``/char/CalendarEventAttendees.xml.aspx``

* __Access mask:__ 4
* __Paramaters:__
    * __eventIDs:__ comma seperated list of event IDs
    * __ids:__ comma seperated list of event IDs

## CharacterSheet
``/char/CharacterSheet.xml.aspx``

* __Access mask:__ 8

## ContactList
``/char/ContactList.xml.aspx``

* __Access mask:__ 16

## ContactNotifications
``/char/ContactNotifications.xml.aspx``

* __Access mask:__ 32

## ContractBids
accessMask = 67108864

## ContractItems
accessMask = 67108864
### Paramaters
contractID:int

## Contracts
accessMask = 67108864
### Paramaters
contractID:int

## FacWarStats
accessMask = 64

## IndustryJobs
accessMask = 128

## IndustryJobsHistory
accessMask = 128

## KillLog
accessMask = 256
### Paramaters
beforeKillID:int

## KillMails
accessMask = 256
### Paramaters
fromID:int, beforeKillID:int, rowCount:int

## Locations
accessMask = 134217728
### Paramaters
ids:"," serperated list

## MailBodies
accessMask = 512
### Paramaters
ids:"," serperated list

## MailingLists
accessMask = 1024

## MailMesages
accessMask = 2048
### Paramaters
fromID:int
rowCount:int

## MarketOrders
accessMask = 4096
### Paramaters
orderID:int

## Medals
accessMask = 8192

## Norifications
accessMask = 16384

## NotificationTexts
accessMask = 32768
### Paramaters
ids:"," serperated list

## PlanetaryColonies
accessMask = 2

## PlanetaryLinks
accessMask = 2
### Paramaters
planetID:int

## PlanetaryPins
accessMask = 2
### Paramaters
planetID:int

## PlanetaryRoutes
accessMask = 2
### Paramaters
planetID:int

## Research
accessMask = 65536

## SkillInTraining
accessMask = 131072

## SkillQueue
accessMask = 262144

## Standings
accessMask = 524288

## UpcomingCalendarEvents
accessMask = 1048576

## WalletJournal
accessMask = 2097152
### Paramaters
fromID
beforeRefID
rowCount

## WalletTransactions
accessMask = 4194304
### Paramaters
beforeTransID
fromID
rowCount

# corp
## AccountBalance

## AssetList

## Blueprints

## ContactList

## ContainerLog

## ContractBids

## ContractItems

## Contracts

## CorporationSheet

## CustomsOffices

## Facilities

## FacWarStats

## IndustryJobs

## IndustryJobsHistory

## KillLog

## KillMails

## Locations

## MarketOrders

## Medals

## MemberMedals

## MemberSecurity

## MemberSecurityLog

## MemberTracking

## OutpostList

## OutpostServiceDetail

## Shareholders

## Standings

## StarbaseDetail

## StarbaseList

## Titles

## WalletJournal

## WalletTransactions

# eve
## AllianceList

## CertificateTree

## CharacterAffiliation

## CharacterID

## CharacterInfo

## CharacterName

## ConquerableStationList

## ErrorList

## FacWarStats

## FacWarTopStats

## OwnerID

## RefTypes

## SkillTree

## TypeName

# map
## FacWarSystems

## Jumps

## Kills

## Sovereignty

# server
## ServerStatus