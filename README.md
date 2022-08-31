# S3 File generator

This has a pretty specific use case, [BuildHub#456](https://github.com/mozilla-services/buildhub/issues/465).  This will generate random files into S3 and every so often generate a [buildhub.json](https://bugzilla.mozilla.org/show_bug.cgi?id=1442306) file. 

## Install and Usage

```
# install dependencies
$ dep ensure 

# build it
$ go build main.go

# run it
$ ./main


# run-time options 
$ ./main --help
Usage of ./main:
    -bucket string
        s3 bucket name (default "buildhub-sqs-test")
    -chance int
        chance out of 100 a buildhub.json file is generated (default 10)
    -delay int
        milliseconds between creating files (default 2000)
    -num int
        how many random files will be generated (default 100)
    -profile string
        aws profile name (default "profile-name")
    -region string
        aws region (default "eu-central-1")
        
## GENERATE FOR A LONG TIME
$ ./main -num 100000 -delay 1000         

## GENERATE LOTS OF FILES QUICKLY
$ ./main -delay 10

## GENERATE LOTS OF BUILDHUB.JSON FILES
$ ./main -chance 80

## Use Profile and Region
$ ./main -delay 1 -num 14000000 --profile aws-profile -bucket bucketname --region eu-west-1
```
