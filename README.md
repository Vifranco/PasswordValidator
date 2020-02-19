AccountPasswordValidator
==================
This solution was developed in order to validate user password according to the given acceptance criteria:
- MinLength > = 9;
- At least one Upper Case;
- At least one Lower case;
- At least one special character;
- At least one digit;

An open RESTful API called as "/SignInAuthentication" was created to receive the user password (string type field of a JSON request) and return a boolean response based on the acceptance criteria listed above.
Two Contracts were created:
- PasswordValidatorRequest: A JSON request is sent to AccountPasswordValidator service based on "PasswordValidator" contract. Example:
{
  "userPassword": "12354686758",
  "userName": "atest11@mailinator.com"
};
- PasswordValidatorResponse: A JSON response is returned based on "SignInAuthResponse" contract. Example:
{	
	"isValid":True,
	"message":"Authorized"
};


Application Execution
--------------------------
The solution was developed over .NetCore framework with Version: 3.0;
The Project Template was Asp.Net Core 3.0 for RESTful HTTP service;

Required SDK\RunTime\FrameWork:

	Language support: 
		C# 8.0-preview
		
	SDK 3.0.100-preview8
	Full version
		3.0.100-preview8-013656
	Visual Studio support
		Visual Studio 2019 (v16.3, latest preview)
	Included runtimes
		.NET Core Runtime 3.0.0-preview8-28405-07
		ASP.NET Core Runtime 3.0.0-preview8-28405-07


The application can be executed over Docker platform in case we have a DockerFile proper configured. 
Note: This release does not support it, only local execution (DebugMode);

We can run the application by Visual Studio 2019 (v16.4, latest preview) with 2 profiles:
- AccountPasswordValidation - DefaultPort configured: 5000/5001. Endpoints for localhost execution:
	- https://localhost:5001/SignInAuthentication;
	- https://localhost:5000/SignInAuthentication;
- IIS Express - Endpoints for localhost execution:
	- https://localhost:44364/SignInAuthentication;

Important files and paths
--------------------------
The following files and folders dependencies must be added in the "AccountPasswordValidatorTests" project dependency in order to UniTest work properly:
- PackageReference Include="Moq" Version="4.13.1"
- PackageReference Include="nunit" Version="3.12.0" 
- PackageReference Include="NUnit3TestAdapter" Version="3.13.0" 
- PackageReference Include="Microsoft.NET.Test.Sdk" Version="16.2.0" 

Test Execution (UniTest)
--------------------------
Unit test can be executed by TestExplorer screen. The test list is:
- Test1_NullPassword;
- Test2_EmptyPassword;
- Test3_OnlyLowerCase_1;
- Test4_OnlyLowerCase_2;
- Test5_OnlyLetters;
- Test6_ValidPassword;
- Test7_OnlyNumber;

Integrated Test by Fiddler (API call)
--------------------------
We can find the "/SignInAuthentication" API call traces for the below scenarios in "...\ViniciusFranco_PasswordValidator_Solution\TestCases - Fiddler_Traces.zip":
- TestCase_1 (NullPasswordField).saz;
- TestCase_2 (OnlyLowerCase_1).saz;
- TestCase_3 (OnlyLowerCase_2).saz;
- TestCase_4 (EmptyPassword).saz;
- TestCase_5 (OnlyLetters).saz;
- TestCase_6 (ValidPassword_1).saz;
- TestCase_7 (ValidPassword_2).saz;
- TestCase_8 (OnlyNumbers).saz;

Note: In case the user doesn't have the Telerik Fiddler tool installed in the his desktop he can open the .saz file as .zip by changing the extension file from ".saz" to ".zip" ;


