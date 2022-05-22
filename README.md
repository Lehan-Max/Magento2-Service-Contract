# Magento2-Service-Contract

  `Magento Service contract` is used for creating certain interfaces & repositories, modules so that it can be compatible with any third-party modules.
  It is a design-pattern. It creates a abstraction layer between business logic && outside world.

    Service contract include: 
    1. Data Interface
    2. Service Interface

    1. Data Interface: Define data interfaces in the Api/Data subdirectory for a module.

    2. Service Interfaces:
      |-----Repository Interface
      |-----Management Interface
      |-----Metadata Interface

      1. `Repository Interface`: Any kind of database operations like insert, delete, update are done using repository interface
      2. `Management Interface`: Any kind of management related operations.

              AccountManagementInterface	Defines the createAccount(), changePassword(), activate(), and isEmailAvailable() functions.
              AddressManagementInterface	Defines the validate() function that validates an address.

      3. `Metadata Interface`: It defines the attributes that are applicable for the attribute. It is data about data. If we create a custom attribute it   will have certain attributes such as is_required, syttem etc. This is called data about data.

  Magento2 has model resource model, then why we still use service-contract?
    Because using model, Resource model most of the methods are depricated & cannot be used with further versions of magento2. So, service contracts were     introduced to overcome this.

   Service-contract implementation is also used for rest Api.

          <route url="/V1/custom/:categoryId/products" method="GET">
            <service class="Vendor\Module\Api\CategoryLinkManagementInterface" method="getAssignedProducts" />
            <resources>
                <resource ref="self"/>
            </resources>
          </route>
  
    resource here is for providing ACL.
    <resource ref="self"/> if resource is reffered as self. for example if api resource is set as self for customer related api, then the customer can                              access only information to him and not any other information related to other customer.
    <resource ref="anonymous"/> Anyone can access.

    Admin user/Integration can acess any information because it has super-privilage
  
   Api Can be accessed in three ways:
      1. `Admin user` - admin authentication token - admin can access any data related to any customers/ any data if acl resource is provided fot that                           admin.
      2. `Customer`   - customer authentication token - used to utilize customer based data like unique price of products based on customers, customer                           cart, wishlist etc.
      3. `Integration token` - Ex: Mobile app

   To generate integration token : System -> Extensions -> Integrations -> Add New Integration
      here we can provide `Resource Access` based on resource we specify in webapi.xml.

   doc block is required because magento code will read the parameter type, return type from the doc block & then provide output.

   ![msc](https://user-images.githubusercontent.com/46992129/168560694-77cc47d1-542b-4501-9881-fc184f7bcf45.jpg)


 
