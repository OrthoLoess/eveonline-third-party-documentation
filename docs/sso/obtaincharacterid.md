Once you have obtained an access token, you can ask the login server for some details of the character that was used to authenticate.

This step is entirely optional, as all you need to authenticate to CREST is the access token and these details can also be obtained from CREST by going CREST root -> TokenDecode -> Character.

To get the character ID from the SSO server make an HTTP GET request to https://login.eveonline.com/oauth/verify that looks like this:

    GET https://login.eveonline.com/oauth/verify HTTP/1.1
    
    User-Agent: ...
    Authorization: Bearer uNEEh...a_WpiaA2
    Host: login.eveonline.com

Important parameters are:

Authorization header - "Bearer" plus the access token from step 2
A successful request will yield a response in JSON format similar to the following:

    {
        CharacterID: 273042051
        CharacterName: "CCP illurkall"
        ExpiresOn: "2014-05-23T15:01:15.182864Z"
        Scopes: " "
        TokenType: "Character"
        CharacterOwnerHash: "XM4D...FoY="
    }
    
The response should be mostly self explanatory except for the CharacterOwnerHash which is a unique hash of the user, the character and salts and secrets all done in secret. But effectively this is unique and doesn't change while the character belongs to the same user account. The CharacterOwnerHash will change if the character is transferred to a different user account and that is the only thing it is useful for, it cannot be used to obtain the user id for a character and it cannot be used to determine if two different characters belong to the same user. 3rd party applications can use this if they are sensitive to characters changing owners, if not this can be safely ignored.