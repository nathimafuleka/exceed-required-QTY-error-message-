# Magento plugin v1.0.0 for Magento v2.4.5

## exceed-required-QTY-error-message

How to display error message when you try to add a product that has less available quantity from selected store view. 

### Changes in code

in Model/IsProductSalableForRequestedQtyCondition
/IsSalableWithReservationsCondition.php file you need to change {STORE_NAME} to the name of the store and ${STORE_NAME} change it to variable you want that can hold the selected store value. 

# installation 
### run the following commands

```
 php bin/magento module:enable errorShow_errorQTY
 
 ```
 
 ```
  php bin/magento setup:upgrade
  
 ```
  
 ```
  php bin/magento setup:di:compile
  
 ```
   
  ```
   php bin/magento setup:static-content:deploy -f 
 ```
     
  ```
  php bin/magento c:c
  ```

 ```
  php bin/magento c:f
  ```

