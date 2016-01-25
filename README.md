# Angular Unit Test with Karma Jasmine


<pre>
1, open gitshell, this will point to your local github folder
2, run command
=git clone   https://github.com/angular/angular-seed.git
this will clone the angular js starter project to local.
3, run command
=npm install
this will get package.json to install all necessary files
4, run command 
=karma start karma.conf.js
chrome browser will open url localhost:9876 karma test page
cmd in cmd prompt will display the progress and logs, such as
Chrome 47.0.2526 (Windows 10 0.0.0): Executed 1 of 1 SUCCESS (0.028 secs / 0.022 secs)
5, file structure

apptest
  index.html - spec run page
  node_module - js packages
  scripts - angular js
  unit-tests - test js files
    controllerspec.js
    servicespec.js
    directivespec.js
    filterspec.js
  e2e-tests - end to end test js files
    protractor.conf.js
    endtoend.js
  karma.conf.js

6, important conf.js

karma.conf.js
   files : [
      'app/bower_components/angular/angular.js',
      'app/bower_components/angular-route/angular-route.js',
      'app/bower_components/angular-mocks/angular-mocks.js',
      'Scripts/app/*.js',
      'unit-tests/*.js'
     ],

here, js in app folder are the js files to be tested, that is , original js file we develop for application
      js in unit-tests folder are the spec.js files used to test , that is, spec js files used to test developed js files
    
7, index.html header is as below used for jasmine test only 

< head>
    < title>< /title>
	< meta charset="utf-8" />
    < script src="Scripts/angular.min.js"></script>
    < script src="Scripts/angular-mocks.js"></script> -----------add for test 
    < script src="Scripts/app/app.js"></script> -----------------here app.js is the js file we want to test
    < script src="unit-tests/controllersSpecs.js"></script> -----here is the spec js file tool we use for testing
< /head>
<body></body> --will display test result from jasmiine

8,  controllersSpecs.js code

describe("test controller", function () {

    beforeEach(module("ngTestApp"));  //before test, we need to let jasmine know ng-app

    var tCtrl, scope;
    
    beforeEach(inject(function ($rootScope, $controller) {
    
        scope = $rootScope.$new();
        tCtrl = $controller('TestCtrl', {$scope: scope});
        
    }));  //before test, we need to inject controller in

    it("test controller", function () {

        expect(scope.title).toEqual("Ng Test"); //then test
        
    });

});

9, ...

</pre>

