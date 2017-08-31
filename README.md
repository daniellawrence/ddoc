Dynamic Documentation
-----

Making documentation friendly & fun...

slides: https://www.slideshare.net/DanielDannyLawrence/dynamic-documentation-srecon-2017

Copy everything below in order to have the wiki page be dynamic!


insert this into the top of the page.
```javascript
{html}
<div ng-app="DDOCApp" ng-controller="DDOCCntl">
{html}
```

insert this into the bottom of the page.

```javascript
{html}
</div>
<script src="https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.6.1/angular.min.js"></script>
<script>
    angular.module('DDOCApp', [], function($locationProvider) {
	      $locationProvider.html5Mode({enabled: true, requireBase: false});
	}).controller('DDOCCntl', function DDOCCntl($scope, $location) {
	$scope.service_name = $location.search()['service_name'] || '{{service-name}}';
					
	// pull out result data
	result_raw = $location.search()['result'] || {};
	$scope.result = angular.fromJson(result_raw)[0];
									  
	// pull out service data
	service_raw = $location.search()['service'] || {};
	$scope.service = angular.fromJson(service_raw)[0];

	});
</script>
{html}
```
