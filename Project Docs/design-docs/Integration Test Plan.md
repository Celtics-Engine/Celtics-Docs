# [Celtics Engine] Integration Test Plan
## Purpose [Test plan]
- Amplify supports Local Mocking and Testing for APIs (AWS AppSync)
- You can either use the Amplify CLI to create a local
	mock server for your API, or you can use the AWS AppSync from within the aws console

* testing of front-end through manual browser-based testing
- this will be done with ng-serve on localhost


## Product Background
- Allow users to share and view game model assets
- [Design doc](https://github.com/Celtics-Engine/Celtics-Docs/blob/cd7b02ea86319f2cdab5f4f4f66ce0768ccc4e0a/Design%20Document.md)

### Use Cases
- Post 3d Assets
- PageState changes


	

# Automated Integration Test Plan
## Use Case: [Post 3d Assets]
### **Test case name: [userPostAssetTest]**
- **Acceptance criteria:**
	- s3 bucket shows file and image uploaded (1 asset consist of 1 file and 1 image)
- **Endpoint(s) tested:**
	- [POST] /bucket/{userID}/{assetID}/images/{imageId}/{filename}
- **GIVEN (Preconditions):**
	- User is authenticated and logged in
	- Upload must be either an image or a file
- **WHEN (Action(s)):**
	- User uploads a file or image to the s3 bucket
- **THEN (Verification steps):**
	- Verify that the file or image is uploaded to the s3 bucket 
- **Is there any clean-up needed for this test?**
	- If local mock server is used, no clean-up needed
	- If AWS AppSync is used, then remove the asset from the database

# Manual Front-end Test Plan
## Use Case: [PageState]
### **Test case name: [PageStateNavigationTest]**
- **GIVEN (Preconditions):**
	- User is authenticated and logged in
	- User is logged out
- **WHEN (Action(s)):**
	- User clicks navigation link in UI component navbar
- **THEN (Verification steps):**
	- Verify that the user is directed to the correct page and that the PageState is set to the correct value for that page
	- If logged out, verify the user does not have the ablitiy to reach PageStates other then login, and explore 