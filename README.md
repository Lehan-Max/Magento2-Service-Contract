# Magento2-Service-Contract

Magento Service contract is used for creating certain interfaces & repositories, modules so that it can be compatible with any third-party modules.

Magento2 has model resource model, then why we still use service-contract?
  Because using model, Resource model most of the methods are depricated & cannot be used with further versions of magento2. So, service contracts were introduced to overcome this.
  
Service-contract implementation is also used for rest Api.

  <route url="/V1/custom/:categoryId/products" method="GET">
    <service class="Vendor\Module\Api\CategoryLinkManagementInterface" method="getAssignedProducts" />
    <resources>
        <resource ref="self"/>
    </resources>
  </route>
  
  resource is for providing ACL.
  
 Api Can be accessed in three ways:
  
