Bring .NET API and EPiServer Commerce module
==================

## What is it?

This is a set of .NET Bring API libraries and module to integrate with EPiServer Commerce. Currently it supports these Bring APIs:
- Shipping Guide API
- Tracking API
- Booking API

## How to install?

Start by installing NuGet packages in you project.

### Shipping Guide API

    Install-Package Geta.Bring.Shipping

### Tracking API

    Install-Package Geta.Bring.Tracking

### Booking API

    Install-Package Geta.Bring.Booking

### EPiServer Commerce module

For EPiServer Commerce you have to install two packages. First package - *Geta.Bring.EPi.Commerce*, should be installed into your EPiServer Commerce Web site:

    Install-Package Geta.Bring.EPi.Commerce

Second package - *Geta.Bring.EPi.Commerce.Manager*, should be installed into your EPiServer Commerce Manager Web site:

    Install-Package Geta.Bring.EPi.Commerce.Manager

## How to use it?

### Shipping Guide API

To start using Shipping Guide API you have to create new *ShippingClient* with provided settings.

    var settings = new ShippingSettings(new Uri("http://test.localtest.me"));
    IShippingClient client = new ShippingClient(settings);

*ShippingSettings* requires at least one parameter - *clientUri*, which is the base URI of your Web site.

To find estimated delivery options you have to call *FindAsync* method with query parameters and type of the estimate.
    
    var query = new EstimateQuery(
        new ShipmentLeg("0484", "5600"),
        PackageSize.InGrams(2500));
    var result = await sut.FindAsync<ShipmentEstimate>(query);

There are three types of estimates:
- *DeliveryEstimate* - returns estimated delivery options,
- *PriceEstimate* - returns estimated price options,
- *ShipmentEstimate* - returns estimated delivery, price and GUI information options.

### Tracking API

### Booking API

### EPiServer Commerce module

## More info about Bring API

### Shipping Guide API

http://developer.bring.com/api/shippingguideapi.html

*Demo*

http://fraktguide.bring.no/fraktguide/demoVelgFraktalternativ.do?from=0484&to=0470&weightInGrams=800&length=10&width=20&height=5&product=servicepakke&product=pa_doren&product=bpakke_dor-dor&product=smaapakker_a-post&product=ekspress09&product=smaapakker_b-post&product=courier_1h&product=minipakke&callbackUrl=http://fraktguide.bring.no/fraktguide/popupCallback.jsp&date=2014-03-17

### Tracking API

http://developer.bring.com/api/trackingapi.html

### Booking API

http://developer.bring.com/api/bookingapi.html