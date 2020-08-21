# dbstruct
dbstruct is a builder to generate column name db from postgres, mysql table into auto generated struct golang

# How to implement this


import to your code
```
go get github.com/mriskyp/dbstruct
```



make sure you have setup generate.yml which consists:
```
generate-dbstruct:
  dbHost : somehost
  dbPort : someport
  dbName : somedbname
  dbUser : someuser
  dbPassword : somepassword
  dbType : somedbtype
  tableName : somedbtablename
  jsonFormat: somejsonformat
```
 
after that, running main.go to complete the process. your autogenerated struct will be shown as output.
it will evaluate any from db information schema and check dependencies.

then, the output will be here
```
---------------auto generated struct---------------

type AutoGeneratedDB struct {
        Id int64 "json:"id" db:"id"`
        CustomerUuid null.String "json:"customerUuid" db:"customer_uuid"`
        CustomerSlug null.String "json:"customerSlug" db:"customer_slug"`
        Email null.String "json:"email" db:"email"`
        UniqueEmail null.String "json:"uniqueEmail" db:"unique_email"`
        Password null.String "json:"password" db:"password"`
        CustomerPhotoUrl null.String "json:"customerPhotoUrl" db:"customer_photo_url"`
        Name null.String "json:"name" db:"name"`
        FirstName null.String "json:"firstName" db:"first_name"`
        LastName null.String "json:"lastName" db:"last_name"`
        CustomerPhone null.String "json:"customerPhone" db:"customer_phone"`
        CustomerGender null.String "json:"customerGender" db:"customer_gender"`
        CustomerBirthday null.String "json:"customerBirthday" db:"customer_birthday"`
        CustomerReward null.Float "json:"customerReward" db:"customer_reward"`
        CustomerRewardInUse null.Float "json:"customerRewardInUse" db:"customer_reward_in_use"`
        IsEmailSent int64 "json:"isEmailSent" db:"is_email_sent"`
        IsGuest null.Int "json:"isGuest" db:"is_guest"`
        EmailVerified null.Int "json:"emailVerified" db:"email_verified"`
        TotalTransaction null.Int "json:"totalTransaction" db:"total_transaction"`
        TotalTransactionValue null.Float "json:"totalTransactionValue" db:"total_transaction_value"`
        IpAddress null.String "json:"ipAddress" db:"ip_address"`
        VerifiedAt null.Time "json:"verifiedAt" db:"verified_at"`
        CreatedAt null.Time "json:"createdAt" db:"created_at"`
        UpdatedAt null.Time "json:"updatedAt" db:"updated_at"`
        LastLogin null.Time "json:"lastLogin" db:"last_login"`
        RememberToken null.String "json:"rememberToken" db:"remember_token"`
}

 query processing time %s 
 52.649216ms
success generate struct%  

```

from the output above, we see that json is camelCase, you may also setup config :
-camelcase format, means that json will be some json:"camelCase"
-underscore format, means that json will be json:"under_score"

example:
-jsonFormat: camelcase
        LastLogin null.Time "json:"lastLogin" db:"last_login"`
-jsonFormat: underscore
        LastLogin null.Time "json:"last_login" db:"last_login"`
  
## Dependencies
```
github.com/ghodss/yaml
github.com/lib/pq
github.com/go-sql-driver/mysql
```

be careful, instead of passing sql.NullString, we want you to also implement null.String from package guregu 

simply just get the package
```
go get gopkg.in/guregu/null.v3
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
