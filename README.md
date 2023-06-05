# Magento plugin v1.0.0 for Magento v2.4.5

## exceed-required-QTY-error-message

How to display error message when you try to add a product that has less available quantity from selected store view. 

### Changes in code

in Model/IsProductSalableForRequestedQtyCondition
/IsSalableWithReservationsCondition.php file you need to change {STORE_NAME} to the name of the store and ${STORE_NAME} change it to variable you want that can hold the selected store value. 

1. <b>If you have couple of stores you can duplicate this line of code and than follow the above changes:</b>

```
if ($requestedQty>$STORE_NAME && $selectedStore == 'STORE_NAME') {
            $errors = [
                $this->productSalabilityErrorFactory->create([
                    'code' => 'is_salable_with_reservations-not_enough_qty',
                    'message' => __('The requested qty exceeds store inventory. %1 units available at STORE_NAME %2.', $STORE_NAME, $selectedStore)
                ])
            ];

            return $this->productSalableResultFactory->create(['errors' => $errors]);
        }
```

2. <b>you can find the attribute code in your admin dashboard and than insert it in this line below and replace the part that says "Attribute_Code ":</b>

```
$STORE_NAME = $product->getResource()->getAttributeRawValue($product->getId(), 'Attribute_Code', $product->getStoreId());
```
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

