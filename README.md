# cookie-util.coffee

       App.Functions.readCookie = (name) ->
        nameEQ = name + "="
        ca = document.cookie.split(";")
        i = 0
        while i < ca.length
          c = ca[i]
          c = c.substring(1, c.length)  while c.charAt(0) is " "
          return c.substring(nameEQ.length, c.length).replace(/"/g, '')  if c.indexOf(nameEQ) is 0
          i++
        ca
        
       App.Functions.setCookie = (cookieName, cookieValue) ->
        today = new Date()
        expire = new Date("2015-01-01 12:00:00")
        document.cookie = cookieName + "=" + escape(cookieValue) + ";expires=" + expire.toGMTString();
     
   
#  cookie-util.coffee
              
      setCookie = (name, value, days) ->
       if days
              date = new Date()
              date.setTime date.getTime() + (days * 24 * 60 * 60 * 1000)
              expires = "; expires=" + date.toGMTString()
       else
              expires = ""
              document.cookie = name + "=" + value + expires + "; path=/"
              
       getCookie = (name) ->
         nameEQ = name + "="
         ca = document.cookie.split(";")
         i = 0
       
         while i < ca.length
           c = ca[i]
           c = c.substring(1, c.length)  while c.charAt(0) is " "
           return c.substring(nameEQ.length, c.length)  if c.indexOf(nameEQ) is 0
           i++
         null
         
       deleteCookie = (name) ->
         setCookie name, "", -1
