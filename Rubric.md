# [Celtics Engine] Project Rubric
	
## Deliverables

[Design Document](https://github.com/Celtics-Engine/Celtics-Docs/blob/master/Project%20Docs/Templates/Design%20Document%20Template.md)


[Team Charter](https://github.com/Celtics-Engine/Celtics-Docs/blob/cd7b02ea86319f2cdab5f4f4f66ce0768ccc4e0a/Team%20Charter.md)

[Team Reflection](https://github.com/Celtics-Engine/Celtics-Docs/blob/cd7b02ea86319f2cdab5f4f4f66ce0768ccc4e0a/Reflection.md)

[Accomplishment Tracking](https://github.com/Celtics-Engine/Celtics-Docs/blob/cd7b02ea86319f2cdab5f4f4f66ce0768ccc4e0a/Accomplishment%20tracking%20template.md)
	
## Technical Learning Objectives
- Amplify  
- Graphql
- Angular

### API Design
```
type Assets @aws_iam @aws_cognito_user_pools @aws_api_key 
{
	id: ID!
	Name: String
	Description: String
	Images: [String]
	AssetFile: String
	FileSize: String
	CompatableEngineVer: [String]
	UserName: String
	UserId: String
	createdAt: AWSDateTime!
	updatedAt: AWSDateTime!
	_version: Int!
	_deleted: Boolean
	_lastChangedAt: AWSTimestamp!
	owner: String
}


type Mutation @aws_iam @aws_cognito_user_pools
{
	createAssets(input: CreateAssetsInput!, condition: ModelAssetsConditionInput): Assets
	updateAssets(input: UpdateAssetsInput!, condition: ModelAssetsConditionInput): Assets
	deleteAssets(input: DeleteAssetsInput!, condition: ModelAssetsConditionInput): Assets
}


type Query @aws_api_key @aws_iam
{
	getAssets(id: ID!): Assets
	listAssets(filter: ModelAssetsFilterInput, limit: Int, nextToken: String): ModelAssetsConnection
	syncAssets(
		filter: ModelAssetsFilterInput,
		limit: Int,
		nextToken: String,
		lastSync: AWSTimestamp
	): ModelAssetsConnection
	searchAssets(
		filter: SearchableAssetsFilterInput,
		sort: [SearchableAssetsSortInput],
		limit: Int,
		nextToken: String,
		from: Int,
		aggregates: [SearchableAssetsAggregationInput]
	): SearchableAssetsConnection
}


type Subscription @aws_subscribe @aws_api_key @aws_iam
{
	onCreateAssets: Assets (mutations: ["createAssets"])
	onUpdateAssets: Assets (mutations: ["updateAssets"])
	onDeleteAssets: Assets (mutations: ["deleteAssets"])
}
```
