**WPM-Get-All-Secured-Items -toSlack.json**<br>
This flow will post all secure items and secure password detials to slack for a certain user. The username and password for the user are collected via a form in the custom values of the flow.
Process:
1. Login as the user to receive a cookie
2. Query for all secure items (notes and passwords) the rowId is returned
3. Query for the secure item details (notes or password) with the rowId
     - If the item is a secure note then loop over the custom parameters fields
     - If the item is a secure password then post all details
