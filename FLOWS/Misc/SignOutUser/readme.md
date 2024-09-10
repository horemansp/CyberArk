This flow will sign out users that belong to a certain role everwhere.<br>
This example uses the role name "cd_user"

Example of a more advanced query:

```
SELECT
  User.DisplayName,
    User.Status,
    User.Email,
    User.MobileNumber as 'Mobile Number',
    Device.Name as 'Mobile App Registered',
    count (OATHTOKEN.Type) as 'OATH Tokens Registered',
    count (U2Fdevice.UserDefinedName) as 'Fido Devices'
FROM
    RoleMember
  LEFT JOIN User on User.ID = SPLIT_PART(RoleMember.ID, '_',1)
  LEFT JOIN DEVICE on Device.OwnerID = SPLIT_PART(RoleMember.ID, '_',1)
  LEFT JOIN OATHTOKEN on OATHTOKEN.UserUuid  = SPLIT_PART(RoleMember.ID, '_',1)
  LEFT JOIN U2FDEVICE on U2fDevice.UserUuid = SPLIT_PART(RoleMember.ID, '_',1)
  
  WHERE RoleMember.ID like CONCAT('%',@Role,'%')
   GROUP By User.ID, User.DisplayName,User.Status,User.Email,User.MobileNumber,Device.Name
 
    ORDER by User.DisplayName asc
```
