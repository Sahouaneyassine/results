# Instructions for my.properties
This file contains all variables that we will need ton run our SCAN Against a target




# Extra authentication parameters

```
auth.loginurl             The URL to the login page. Required.
auth.username             A valid username. Required.
auth.password             A valid password. Required.
key_field_username        By what u want to get the field ( value , id , name ) <input name,value,id= />
key_field_password        By what u want to get the field ( value , id , name ) <input name,value,id= />
key_field_first_submit    By what u want to get the field ( value , id , name ) <input name,value,id= />
key_field_submit          By what u want to get the field ( value , id , name ) <input name,value,id= />

submit_button_input       The submit is ( button , input ) <button/> ? <input/>

id_field_username
id_field_password
id_field_first_submit
id_field_submit


auth.username_field       The HTML name or id attribute of the username field.
auth.password_field       The HTML name or id attribute of the password field.
auth.submit_field         The HTML name or id attribute of the submit field.
auth.otp_field            The HTML name or id attribute of the OTP field.
auth.first_submit_field   The HTML name or id attribute of the first submit field (in case of username -> next page -> password -> submit).
auth.submitaction         "Click" or "Submit" to click the login button or submit the form.
auth.display              True or False, indicate if the the webdriver should run in Headless mode.
auth.exclude              Comma separated list of excluded URL's (regex). Default: (logout|uitloggen|afmelden|signout)
auth.include              Comma separated list of included URL's (regex). Default: only the target URL and everything below it.
auth.check_delay          How long to wait after submitting the form.
auth.check_element        Element to look for to verify login completed.
```
