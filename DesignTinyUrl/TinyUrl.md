Requirement :
              Deisgn a URLShortner system which take a long url and generates a short Url.Design Should be scalable.
              
              
Let's Design system Which is not scalable first.

[A-Z,a-z,0-9]  = 62 character.
shorlurl has 7 bit long.62^7 = 3.5 Trillion = 2^43

              
Database Design :
        ID                  LONG        AUTO_INCREAMENT                     
        ActualUrl           String      UNIQUE  NOT NULL
        ShortUrl            String       UNIQUE NULL
        
API  :
      POST  /urlShortner/generateShortUrl   longUrl
      GET    /urlShortner/lookup?shortUrl=shortUrl
      
      
      generateShortUrl :
              insert longurl into database.fetch ID of the Row.convert this ID into base62 hash.Store this hash into the same row and return the bitly.com/hash
      lookUp :
            reverse generate ID using the hash using Basg62.using this ID fetch long url and return it.
    see https://github.com/Abhishek18garg/DesignSystem/blob/master/DesignTinyUrl/ShortUrl.java    for conversion.
    
    
    
   Other Designs:
     hash = md5(longUrl)   .take hash's 43 bits.convert this 43 bit into base10.then base 10 to base 62.
      nowStore    (longUrl,base62(base10(md5(longUrl) of 43bits))).
 
  
        
        
              
