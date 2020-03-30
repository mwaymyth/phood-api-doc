Reference
=============

Query
--------


*me*
^^^^^^
Gets details on the current user.

output:
    Me_!

*paymentMethods*
^^^^^^^^^^^^^^^^
List the current user's payment methods 

output:
    [PaymentMethod_!]!

*order*
^^^^^^^
Get a specific order

**args**:
    **id**: ID_!

output:
    Order_!

*orders*
^^^^^^^^
Get the current user's orders.

output:
    [Order_!]!

Mutation
----------------

*authenticate*
^^^^^^^^^^^^^^^^
Authenticate and receive an authorization token.

**args**:
    |   **email**: String_!
    |   **password**: String_!

output:
    String_!


*authenticateWithGoogle*
^^^^^^^^^^^^^^^^^^^^^^^^
Authenticate with google and receive an authorization token.

**args**:
    |   **accessToken**: String_!

output:
    String_!


*authenticateWithFacebook*
^^^^^^^^^^^^^^^^^^^^^^^^^^
Authenticate with facebook and receive an authorization token.

**args**:
    |   **accessToken**: String_!

output:
    String_!


*authenticateWithTwitter*
^^^^^^^^^^^^^^^^^^^^^^^^^
Authenticate with Twitter and receive an authorization token.

**args**:
    |   **secret**: String_!
    |   **token**: String_!

output:
    String_!


*authenticateWithForgotPasswordToken*
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Authenticate with a forgot password token and receive an authorization token

**args**
    **token**: String_!

output:
    String_!


*createUser*
^^^^^^^^^^^^^^^^
Create a new User

**args**:
    |   **email**: String_
    |   **name**: String_
    |   **password**: String_

output:
    User_!

*updateUser*
^^^^^^^^^^^^^^^^
Update User information.

**args**:
    |   **email**: String_
    |   **name**: String_
    |   **password**: String_
    |   **phone**: String_

output:
    Me_!

*sendForgotPasswordEmail*
^^^^^^^^^^^^^^^^^^^^^^^^^
Send a forgot password email to a specified email address.

**args**:
    **email**: String_!

output:
    Boolean_!


*placeOrder*
^^^^^^^^^^^^

**args**:
    |    **orderItems**: [OrderItemInput_!]!
    |    **specialInstructions**: String_

output:
    Order_


*reorder*
^^^^^^^^^
Reorder by orderId.

**args**:
    **orderID**: String_!

output:
    Order_


*registerDevice*
^^^^^^^^^^^^^^^^

**args**:
    **fcmToken**: String_!

output:
    Device_


*cashOut*
^^^^^^^^^^^^^^^^

output:
    Payment_!

*createPaymentMethod*
^^^^^^^^^^^^^^^^^^^^^^

**args**:
    **input**: PaymentMethodInput_!

output:
    PaymentMethod_

*deletePaymentMethod*
^^^^^^^^^^^^^^^^^^^^^

**args**:
    **input**: DeletePaymentMethodInput_!

output:
    PaymentMethod_


Objects
----------

.. _Me:

*Me*
^^^^^
Details about the current user.

fields:
    |    **avatarUrl**: String_!
    |    **defaultAddressId**: String_
    |    **driver**: Driver_
    |    **email**: String_
    |    **id**: ID_!
    |    **insertAt**: DateTime_!
    |    **name**: String_
    |    **phone**: String_
    |    **updatedAt**: DateTime_!
    |    **username**: String_

.. _Payment:

*Payment*
^^^^^^^^^

fields:
    |    **id**: ID_
    |    **insertedAt**: DateTime_!
    |    **total**: Float_!
    |    **user**: User_!


.. _PaymentMethod:

*PaymentMethod*
^^^^^^^^^^^^^^^
Details about payment methods.

fields:
    |    **cardType**: String_
    |    **id**: ID_
    |    **insertAt**: DateTime_!
    |    **month**: Int_!
    |    **name**: String_!
    |    **number**: String_!
    |    **token**: String_
    |    **updateAt**: DateTime_!
    |    **year**: Int_!


.. _PaymentMethodInput:

*PaymentMethodInput*
^^^^^^^^^^^^^^^^^^^^
Arguments for creating a payment method.

fields:
    |    **cardType**: String_!
    |    **month**: Int_!
    |    **name**: String_!
    |    **number**: String_!
    |    **year**: Int_!


.. _DeletePaymentMethodInput:

*DeletePaymentMethodInput*
^^^^^^^^^^^^^^^^^^^^^^^^^^
Arguments for deleting a payment method

fields:
    **paymentMethodID**: String_!



.. _Driver:

*Driver*
^^^^^^^^
Details about the Driver.

fields:
    |    **availability**: AvailabilityStatus_!
    |    **id**: ID_
    |    **insertAt**: DateTime_!
    |    **performance**: DriverPerformance_!
    |    **updatedAt**: DateTime_!
    |    **user**: User_!

.. _DriverPerformance:

*DriverPerformance*
^^^^^^^^^^^^^^^^^^^
Details on the Drivers performance.

fields:
    |    **lastDay**: [DriverPerformanceData_!]!
    |    **lastMonth**: [DriverPerformanceData_!]!
    |    **lastWeek**: [DriverPerformanceData_!]!

.. _DriverPerformanceData:

*DriverPerformanceData*
^^^^^^^^^^^^^^^^^^^^^^^
fields:
    |    **average**: String_!
    |    **my**: String_!
    |    **title**: String_!


.. _User:

*User*
^^^^^^
fields:
    |    **avatarUrl**: String_!
    |    **id**: ID_!
    |    **insertAt**: DateTime_!
    |    **name**: String_
    |    **phone**: String_
    |    **updatedAt**: DateTime_!
    |    **username**: String_


.. _UserLocation:

fields:
    |    **address**: String_!
    |    **latitude**: Float_!
    |    **longitude**: Float_!


.. _Device:

*Device*
^^^^^^^^
A device for a user.

fields:
    |   **id**: ID_!


.. _Order:

*Order*
^^^^^^^^
Details on a order.

fields:
    |    **delivery**: Delivery_!
    |    **deliveryFee**: Float_!
    |    **id**: ID_!
    |    **insertedAt**: DateTime_!
    |    **items**: [OrderItem_!]!
    |    **itemsSummary**: String_
    |    **orderNumber**: String_
    |    **paymentMethod**: PaymentMethod_
    |    **rating**: Rating_
    |    **restaurant**: Restaurant_!
    |    **status**: OrderStatus_!
    |    **subtotal**: Float_!
    |    **tax**: Float_
    |    **tip**: Float_
    |    **total**: Float_!
    |    **updatedAt**: DateTime_!
    |    **user**: User_!


.. _OrderItem:

*OrderItem*
^^^^^^^^^^^
fields:
    |    **id**: ID_!
    |    **itemPrice**: Float_!
    |    **menuItem**: MenuItem_
    |    **order**: Order_!
    |    **quantity**: Int_
    |    **total**: Float_!


.. _OrderItemInput:

*OrderItemInput*
^^^^^^^^^^^^^^^^^
Arguments for order item input.

fields:
    |    **items**: [OrderItemModifierInput_!]!
    |    **menutItemId**: ID_!
    |    **quantity**: Int_!
    |    **specialInstructions**: String_


.. _OrderItemModifierInput:

*OrderItemModifierInput*
^^^^^^^^^^^^^^^^^^^^^^^^^
Arguments for order item modifier input.

fields:
    **itemId**: ID_!

.. _Menu:

*Menu*
^^^^^^
fields:
    |    **description**: String_
    |    **id**: ID_
    |    **insertedAt**: DateTime_
    |    **menuSection**: [MenuSection_!]!
    |    **name**: String_
    |    **toGold**: String_
    |    **updatedAt**: DateTime_


.. _MenuItem:

*MenuItem*
^^^^^^^^^^
fields:
    |    **class**: String_
    |    **description**: String_
    |    **displayPrice**: String_
    |    **id**: ID_!
    |    **includedGroups**: [MenuItemGroup_!]
    |    **isHealthy**: Boolean_!
    |    **menuItemGroup**: MenuItemGroup_!
    |    **menuSection**: MenuSection_!
    |    **name**: String_
    |    **price**: Decimal_
    |    **primaryImageUrl**: String_
    |    **toGold**: String_


.. _MenuItemGroup:

*MenuItemGroup*
^^^^^^^^^^^^^^^
fields:
    |    **class**: String_
    |    **description**: String_
    |    **displayPrice**: String_
    |    **id**: ID_!
    |    **isHealthy**: Boolean_!
    |    **maxChoices**: Decimal_
    |    **menuItems**: [MenuItem_!]
    |    **price**: Decimal_
    |    **primaryImageUrl**: String_
    |    **title**: String_
    |    **toGold**: String_

.. _MenuSection:

*MenuSection*
^^^^^^^^^^^^^^^
fields:
    |    **description**: String_
    |    **id**: ID_!
    |    **insertAt**: DateTime_!
    |    **isHidden**: Boolean_
    |    **menuItems**: [MenuItem_!]
    |    **title**: String_
    |    **toGold**: String_
    |    **updatedAt**: DateTime_

.. _Delivery:

*Delivery*
^^^^^^^^^^
fields:
    |    **deliveryLocation**: DeliveryLocation_!
    |    **deliveryLocations**: [DeliveryLocation_!]!
    |    **driver**: Driver_!
    |    **eta**: String_!
    |    **id**: ID_
    |    **insertedAt**: DateTime_!
    |    **order**: Order_
    |    **userLocation**: UserLocation_!
    |    **vote**: DeliveryVote_

.. _DeliveryLocation:

*DeliveryLocation*
^^^^^^^^^^^^^^^^^^
fields:
    |    **eta**: String_!
    |    **id**: ID_!
    |    **insertedAt**: DateTime_!
    |    **latitude**: Float_!
    |    **longitude**: Float_!
    |    **status**: String_!


.. _DeliveryVote:

*DeliveryVote*
^^^^^^^^^^^^^^
fields:
    |    **delivery**: Delivery_!
    |    **id**: ID_!
    |    **vote**: Int_!


.. _Rating:

*Rating*
^^^^^^^^
fields:
    |    **comment**: String_
    |    **id**: ID_
    |    **insertedAt**: DateTime_!
    |    **order**: Order_!
    |    **restaurant**: Restaurant_!
    |    **value**: Decimal_!

.. _Restaurant:

*Restaurant*
^^^^^^^^^^^^^
fields:
    |    **address1**: String_!
    |    **address2**: String_]!
    |    **city**: String_!
    |    **contact**: String_!
    |    **deliveryFee**: Decimal_
    |    **description**: String_
    |    **email**: String_
    |    **hours**: String_
    |    **id**: ID_
    |    **imageUrl**: String_
    |    **insertedAt**: DateTime_!
    |    **latitude**: Float_
    |    **longitude**: Float_
    |    **menus**: [Menu_!]!
    |    **name**: String_
    |    **phone**: String_
    |    **state**: String_
    |    **updatedAt**: DateTime_!
    |    **zip**: String_

Scalars
---------

.. _String:

*String*
^^^^^^^^
Represents textual data, represented as UTF-8 character sequences. 
The String type is most often used by GraphQL to represent free-form human-readable text.

.. _DateTime:

*DateTime*
^^^^^^^^^^
Represents a date and time in the UTC timezone. 
The DateTime appears in a JSON response as an ISO8601 formatted string, including UTC timezone ("Z"). 
The parsed date and time string will be converted to UTC and any UTC offset other than 0 will be rejected.

.. _ID:

*ID*
^^^^
Represents a unique identifier, often used to refetch an object or as key for a cache. The ID type appears in a JSON response as a String; however, it is not intended to be human-readable. 
When expected as an input type, any string (such as "4") or integer (such as 4) input value will be accepted as an ID.

.. _Int:

*Int*
^^^^^
Represents non-fractional signed whole numeric values. Int can represent values between -(2^31) and 2^31 - 1.

.. _Float:

*Float*
^^^^^^^
Represents signed double-precision fractional values as specified by IEEE 754.

.. _Decimal:

*Decimal*
^^^^^^^^^
Represents signed double-precision fractional values parsed by the Decimal library. 
The Decimal appears in a JSON response as a string to preserve precision.

.. _Boolean:

*Boolean*
^^^^^^^^^
Represents **true** or **false**.

Enum
------

.. _AvailabilityStatus:

*AvailabilityStatus*
^^^^^^^^^^^^^^^^^^^^
Drivers Availability Status.

values:
    |   offline
    |   online

.. _OrderStatus:

*OrderStatus*
^^^^^^^^^^^^^
Order Status.

values:
    |   delivered
    |   delivering
    |   pending
    |   processed
