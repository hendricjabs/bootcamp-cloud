# Bootcamp Cloud: Cloud Formation Count Macro
This Macro for Cloud Formation enables the use of the count-Functionality. The count functionality replicates a resource which has the CountProperty defined.
To use this template run the count-macro.yaml as Stack in AWS Cloud Formation.
There are two parameters to set:
1. Stack name = The name of the Stack and the Macro
2. CountProperty = The keyword which indicates the count. e.g. Count
3. CountPlaceholder = The placeholder which will be replaced by the current index of the resource e.g. #Count#

If you want to use this macro in your template just define the Transform Property with the stackname. Given you deployed the count-macro.yaml with the stack name CountMacro the Transform statement at the end of your template will look as follwing:
```
Transform: [CountMacro]
```
After that you can use the CountProperty to replicate your resource.
If you want to create four S3 Buckets with the names test-0, test-1, test-2 and test-3 just define it as following, where #Count# can differ depending on your CountPlaceholder parameter:

```yaml
S3Bucket:
    Type: "AWS::S3::Bucket"
    Properties:
      BucketName: "test-#Count#"
    Count: 4
```

You can find a full working example in count-macro-example.yaml.

Check out bootcamp-cloud.de other cool projects on AWS.
