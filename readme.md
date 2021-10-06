AWS S3 with PHP - Amazon Web Services End to End Guide
======================================================

* ***Actions on the deployment of the project:***

- Making a new project aws-s3-php_ktcoder.loc:
																	
sudo chmod -R 777 /var/www/AWS_PHP/aws-s3-php_ktcoder.loc

//!!!! .conf
sudo cp /etc/apache2/sites-available/test.loc.conf /etc/apache2/sites-available/aws-s3-php_ktcoder.loc.conf
		
sudo nano /etc/apache2/sites-available/aws-s3-php_ktcoder.loc.conf

sudo a2ensite aws-s3-php_ktcoder.loc.conf

sudo systemctl restart apache2

sudo nano /etc/hosts

cd /var/www/AWS_PHP/aws-s3-php_ktcoder.loc

- Deploy project:

	`git clone << >>`
	
	_+ Сut the contents of the folder up one level and delete the empty one._

	`composer install`	

---

Keith, the Coder

[AWS S3 with PHP - Amazon Web Services End to End Guide (24:30)]( https://www.youtube.com/watch?v=aPBFqDIIPYE&ab_channel=Keith%2CtheCoder )

This is a tutorial on how to use Amazon Web Services (AWS) S3 bucket with PHP. 
This guide includes setting up an S3 bucket with proper IAM users and permissions, uploading files (public file upload and private file upload),
viewing your content on the AWS S3 dashboard, and accessing your content privately. You may be wondering how to share your files in a private way, this vide is a guide for PHP users.

Subscribe because I will be launching a view for doing this using Python, and Node.js. I will also update my AWS S3 Bucket Setup video.

Code used:

S3 Bucket and IAM User Setup Repo - 
<https://github.com/keithweaver/python-aws-s3>

Upload image using form submission to AWS S3 with PHP - 
<https://gist.github.com/keithweaver/70eb06d98b008113ce97f6148fbea83d>

Open AWS S3 File Privately with PHP - 
<https://gist.github.com/keithweaver/87c5af35f70aac32b4e621fc9fa3b568>

Other S3 Bucket Videos:

Setting up Amazon Web Services (AWS) S3 Bucket and IAM User - 
<https://youtu.be/v33Kl-Kx30o>

Uploading a File to Amazon Web Services (AWS) S3 Bucket with PHP - 
<https://youtu.be/CsiO338whtw>

Uploading a File to Amazon Web Services (AWS) S3 Bucket with Python - 
<https://youtu.be/mtBR-PajgbM>

Uploading a Public File to Amazon Web Services (AWS) S3 Bucket with Python - 
<https://youtu.be/8ObF8Qnw_HQ>

[(1:10)]( https://youtu.be/aPBFqDIIPYE?t=70 )

S3 Bucket and IAM User Setup Repo - 
<https://github.com/keithweaver/python-aws-s3>

[(1:15)]( https://youtu.be/aPBFqDIIPYE?t=75 )

Upload image using form submission to AWS S3 with PHP - 
<https://gist.github.com/keithweaver/70eb06d98b008113ce97f6148fbea83d>

[(1:20)]( https://youtu.be/aPBFqDIIPYE?t=80 )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/aws/1.png )

Open AWS S3 File Privately with PHP - 
<https://gist.github.com/keithweaver/87c5af35f70aac32b4e621fc9fa3b568>

[(2:40)]( https://youtu.be/aPBFqDIIPYE?t=160 )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/aws/2.png ) `Create Bucket.`

[(2:58)]( https://youtu.be/aPBFqDIIPYE?t=178 )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/aws/3.png )

[(3:09)]( https://youtu.be/aPBFqDIIPYE?t=189 ) `IAM`.

[(3:32)]( https://youtu.be/aPBFqDIIPYE?t=212 ) `IAM-> Users-> Add User`. 

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/aws/4.png )

`Next...`

[(3:40)]( https://youtu.be/aPBFqDIIPYE?t=220 ) `"README.MD"`.

- Bucket Name
												
- User Name

```
examplephp-endtoend

examplephp-endtoend-user
```

[(4:03)]( https://youtu.be/aPBFqDIIPYE?t=243 ) `Create User`. `Access key ID`, `Secret access key`. After leaving this window, the `Secret access key` is no longer shown in the system. 

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/aws/5.png )

- Access key ID
												
- Secret access key
												
```
AWS_APPKEY=
AWS_SECRET=												
```

`Close`.

[(4:26)]( https://youtu.be/aPBFqDIIPYE?t=266 ) - Take the user ID, `User ARN`, Amazon Resource Name (ARN) and the `Bucket ARN`.

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/aws/6.png )

- User ARN

- Bucket ARN
						
[(4:46)]( https://youtu.be/aPBFqDIIPYE?t=286 )
_"Set your `Bucket Policy` to be the same as below. Change `arn:aws:iam::281979644754:user/sample-user` to be your `User ARN`. Also change `arn:aws:s3:::img-bucket-00123` to your `Bucket ARN`. The bucket `ARN` is above the textarea."_

<https://github.com/keithweaver/python-aws-s3>

```
{
    "Version": "2012-10-17",
    "Id": "Policy1488494182833",
    "Statement": [
        {
            "Sid": "Stmt1488493308547",
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::522751208087:user/examplephp-endtoend-user"
            },
            "Action": [
                "s3:ListBucket",
                "s3:ListBucketVersions",
                "s3:GetBucketLocation",
                "s3:Get*",
                "s3:Put*"
            ],
            "Resource": "arn:aws:s3:::examplephp-endtoend"
        }
    ]
}
```

`Save changes`.

[(5:13)]( https://youtu.be/aPBFqDIIPYE?t=313 )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/aws/7.png )

[(5:30)]( https://youtu.be/aPBFqDIIPYE?t=330 )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/aws/8.png )

_"Click CORS configuration and add the following policy:"_

```
<?xml version="1.0" encoding="UTF-8"?>
<CORSConfiguration xmlns="http://s3.amazonaws.com/doc/2006-03-01/">
  <CORSRule>
    <AllowedOrigin>*</AllowedOrigin>
    <AllowedMethod>GET</AllowedMethod>
    <AllowedMethod>POST</AllowedMethod>
    <AllowedMethod>PUT</AllowedMethod>
    <MaxAgeSeconds>3000</MaxAgeSeconds>
    <AllowedHeader>Authorization</AllowedHeader>
  </CORSRule>
</CORSConfiguration>
```

`Save changes`.

Error:
_"The CORS configuration must be written in valid JSON."_ 

API Response
_"Expected params CORS.configuration.CORSRules to be an Array."_ 

<https://question-it.com/questions/2173028/amazon-s3-nevozmozhno-ustanovit-politiku-cors>

```
[
    {
        "AllowedHeaders": [
            "*"
        ],
        "AllowedMethods": [
            "PUT",
            "POST",
            "DELETE"
        ],
        "AllowedOrigins": [
            "http://www.example.com"
        ],
        "ExposeHeaders": []
    },
    {
        "AllowedHeaders": [],
        "AllowedMethods": [
            "GET"
        ],
        "AllowedOrigins": [
            "*"
        ],
        "ExposeHeaders": []
    }
]
```

`Save changes`.

_"Reopen the IAM dashboard"._

[(5:54)]( https://youtu.be/aPBFqDIIPYE?t=354 ) "`Open your new user.`"

_"Click on the New inline policy"_

[(6:04)]( https://youtu.be/aPBFqDIIPYE?t=364 )
_"Update the policy to be as follows:"_

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListAllMyBuckets",
                "s3:PutObject",
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::*"
            ]
        }
    ]
}
```

[(6:13)]( https://youtu.be/aPBFqDIIPYE?t=373 )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/aws/9.png )

[(6:21)]( https://youtu.be/aPBFqDIIPYE?t=381 )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/aws/10.png )

[(7:38)]( https://youtu.be/aPBFqDIIPYE?t=458 ) `index.php`

[(7:50)]( https://youtu.be/aPBFqDIIPYE?t=470 ) `Hello world!!!;)`

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/firefox/1.png )

[(8:15)]( https://youtu.be/aPBFqDIIPYE?t=495 )

<https://www.w3schools.com/php/php_file_upload.asp>

[(8:26)]( https://youtu.be/aPBFqDIIPYE?t=506 ) `index.php`:

```html
<!DOCTYPE html>
<html>
<body>

<form action="upload.php" method="post" enctype="multipart/form-data">
  Select image to upload:
  <input type="file" name="fileToUpload" id="fileToUpload">
  <input type="submit" value="Upload Image" name="submit">
</form>

</body>
</html>
```

[(9:15)]( https://youtu.be/aPBFqDIIPYE?t=555 )

`In Terminal`:

	cd /var/www/AWS_PHP/aws-s3-php_ktcoder.loc
	
	composer require aws/aws-sdk-php

[(9:40)]( https://youtu.be/aPBFqDIIPYE?t=580 ) `upload.php`: `Copy` & `Paste`.

Upload image using form submission to AWS S3 with PHP - 
<https://gist.github.com/keithweaver/70eb06d98b008113ce97f6148fbea83d>

[(10:25)]( https://youtu.be/aPBFqDIIPYE?t=625 ) `Edit`:
	
```php	
require './vendor/autoload.php';
...

	// AWS Info
$bucketName = 'SUB_YOUR_BUCKET_NAME_IN';
$IAM_KEY = 'SUB_YOUR_IAM_KEY_IN';
$IAM_SECRET = 'SUB_YOUR_IAM_SECRET_IN';
...

'region'  => 'eu-north-1'
...

$pathInS3 = 'https://s3.eu-north-1.amazonaws.com/' . $bucketName . '/' . $keyName;
```

[(11:10)]( https://youtu.be/aPBFqDIIPYE?t=670 )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/firefox/2.png )

[(11:40)]( https://youtu.be/aPBFqDIIPYE?t=700 )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/firefox/3.png )

[(11:46)]( https://youtu.be/aPBFqDIIPYE?t=706 )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/aws/11.png )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/aws/12.png )

[(12:00)]( https://youtu.be/aPBFqDIIPYE?t=720 ) `Edit`:

```php	
$keyName = 'test_example/' . basename($_FILES["fileToUpload"]['name']);
```

[(12:40)]( https://youtu.be/aPBFqDIIPYE?t=760 ) `Go back. Delete test_example folder`.

[(12:45)]( https://youtu.be/aPBFqDIIPYE?t=765 ) `Upload again`.

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/firefox/4.png )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/firefox/3.png )

[(13:15)]( https://youtu.be/aPBFqDIIPYE?t=795 ) `Download. Open`.

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/aws/13.png )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/aws/14.png )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/aws/15.png )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/aws/16.png )

[(13:40)]( https://youtu.be/aPBFqDIIPYE?t=820 ) `Access Denied`.

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/firefox/5.png )

[(15:25)]( https://youtu.be/aPBFqDIIPYE?t=925 ) `phpMyAdmin. s3DB database, s3Files table`.

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/firefox/6.png )

[(17:30)]( https://youtu.be/aPBFqDIIPYE?t=1050 ) `Save file to files table`...

```php
// Save file to files table - TODO

// Create access code

$ACCESS_CODE = '1234567';

$con = mysqli_connect('localhost', 'root', 'root', 's3DB' ) or die('Error: Unable to connect');

mysqli_query($con, "INSERT INTO s3Files (s3FilePath, accessCode) VALUES ('$keyName', '$ACCESS_CODE')") or die('error: not able to save');
```

[(17:58)]( https://youtu.be/aPBFqDIIPYE?t=1078 ) `Upload`.

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/firefox/7.png )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/aws/3.png )

[(18:23)]( https://youtu.be/aPBFqDIIPYE?t=1103 )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/aws/17.png )

[(18:28)]( https://youtu.be/aPBFqDIIPYE?t=1108 )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/firefox/8.png )

[(18:49)]( https://youtu.be/aPBFqDIIPYE?t=1129 ) `get.php`: `Copy` & `Paste`.

Open AWS S3 File Privately with PHP - 
<https://gist.github.com/keithweaver/87c5af35f70aac32b4e621fc9fa3b568>

```php 
$BUCKET_NAME = '';
$IAM_KEY = '';
$IAM_SECRET = '';

require './vendor/autoload.php';
...

// Connect to database
$con = mysqli_connect('localhost', 'root', 'root', 's3DB' ) or die('Error: Unable to connect');  
// Verify valid access code
$result = mysqli_query($con, "SELECT * FROM s3Files WHERE accessCode='$accessCode'") or die("Error: Invalid request");
...

'region'  => 'eu-north-1'
```

[(20:55)]( https://youtu.be/aPBFqDIIPYE?t=1255 )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/firefox/9.png )

[(22:10)]( https://youtu.be/aPBFqDIIPYE?t=1330 )

<https://stackoverflow.com/questions/3102226/how-to-set-name-of-file-downloaded-from-browser>

[(22:45)]( https://youtu.be/aPBFqDIIPYE?t=1365 ) `Reload Page`.

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/firefox/10.png )

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/firefox/11.png )

[(22:56)]( https://youtu.be/aPBFqDIIPYE?t=1376 )
_` .../get.php?c=123456`_

![screenshot of sample]( https://github.com/mslobodyanyuk/aws-s3-php_ktcoder/blob/main/public/images/firefox/12.png )

#### Useful links:

Keith, the Coder

[AWS S3 with PHP - Amazon Web Services End to End Guide]( https://www.youtube.com/watch?v=aPBFqDIIPYE&ab_channel=Keith%2CtheCoder )

S3 Bucket and IAM User Setup Repo - 
<https://github.com/keithweaver/python-aws-s3>

Upload image using form submission to AWS S3 with PHP - 
<https://gist.github.com/keithweaver/70eb06d98b008113ce97f6148fbea83d>

Open AWS S3 File Privately with PHP - 
<https://gist.github.com/keithweaver/87c5af35f70aac32b4e621fc9fa3b568>

---

<https://www.w3schools.com/php/php_file_upload.asp>

Possible Errors.

<https://question-it.com/questions/2173028/amazon-s3-nevozmozhno-ustanovit-politiku-cors>
