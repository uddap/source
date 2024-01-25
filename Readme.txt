pip install -r requirements.txt --upgrade

pip install django-admin-honeypot-updated-2021
pip install django-storages
pip install django-requests
python -m pip install Pillow
ERRORs
ERR-ModuleNotFoundError: No module named 'admin_honeypot'
solution-admin-honeypot module available only inside virtual environment
ERR- File "C:\Users\chpre\OneDrive\Desktop\ushop\env\lib\site-packages\admin_honeypot\models.py", line 2, in <module>
    from django.utils.translation import ugettext_lazy as _
ImportError: cannot import name 'ugettext_lazy' from 'django.utils.translation' (C:\Users\chpre\OneDrive\Desktop\ushop\env\lib\site-packages\django\utils\translation\__init__.py)
SOLUTION--uninstall django-admin-honeypot-updated-2021 and reinstall


ERR-botocore.exceptions.ClientError: An error occurred (AccessControlListNotSupported) when calling the PutObject operation: The bucket does not allow ACLs
SOLUTION- in settings.py
# AWS_DEFAULT_ACL = 'public-read'
AWS_DEFAULT_ACL = None
https://stackoverflow.com/questions/54788998/djangoaws-s3-botocore-exceptions-clienterror-an-error-occurred-accessdenied
SOLUTION-2
If anyone is still having these issues, The problem is on the AWS S£ bucket and You can fix the problem by enabling ACL on the s3 bucket. To do that,
Go to your S3 Bucket>Permissions Tab
Scroll down to Object Ownership and click on Edit
Change the settings from ACL disabled to ACL enabled and save changes
ERRORs
chpre@LAPTOP-SUK148A8 MINGW64 ~/OneDrive/Desktop/ushop (master)
$ eb init -p python-3.9 django-ushop-app
ERROR: MaxRetriesError - Max retries exceeded for ResponseParserErrorsUnable to parse response (no element found: line 1, column 0), invalid XML received. Further retries may succeed:
b''
Unable to parse response (no element found: line 1, column 0), invalid XML received. Further retries may succeed:
b''
solutiuon-1 or anyone who may be stuck in this issue, the solution is to go to ~/%USERNAME%/.aws and delete the 'config' file there, then try running eb init again.
SOLUTION:Go to C:\Users\YOUR_USERNAME\.aws and delete the 'config' file there, then try running eb init again.
eb init -p python-3.8 django-ushop-app


install ebwscli

hpre@LAPTOP-SUK148A8 MINGW64 ~/OneDrive/Desktop/ushop (master)
$ source env/Scripts/activate
(env)
chpre@LAPTOP-SUK148A8 MINGW64 ~/OneDrive/Desktop/ushop (master)
$ python manage.py collectstatic

You have requested to collect static files at the destination
location as specified in your settings.

This will overwrite existing files!
Are you sure you want to do this?

Type 'yes' to continue, or 'no' to cancel: yes

0 static files copied, 497 unmodified.
(env)
chpre@LAPTOP-SUK148A8 MINGW64 ~/OneDrive/Desktop/ushop (master)
$

deactivate venv before deploying using ebcli
eb init -p python-3.9.13 django-ushop-app
aws AWS_ACCESS_KEY_IDid and SECRET_KEY


ISSUE- eb create django-ushop-env
Starting environment deployment via CodeCommit
ERROR: InvalidParameterValueError - "Error making request to CodeCommit: Could not retrieve 30b2a0e3701244c667ef0c3e01004863f7fb63d6 (Service: AWSCodeCommit;
Status Code: 400; Error Code: CommitIdDoesNotExistException; Request ID: 6a435ff7-25a3-444b-90cb-3b1804ad51db; Proxy: null)"

SOLUTION- select No

Issue- RuntimeWarning: Got an error checking a consistent migration history performed for database connection 'default': (2002, "Can't connect to server on '128.0.0.1' (10060)")


----AWS ISSUES

Both S3 bucket and key must be specified.

Invalid option specification (Namespace: 'aws:elasticbeanstalk:managedactions', OptionName: 'ManagedActionsEnabled'): Managed platform updates require enhanced
health reporting (option SystemType in namespace aws:elasticbeanstalk:healthreporting:system).

Unable to download from S3 location (Bucket: s3 Key: s3/buckets/my-ushop-s3bucket). Reason: Bad Request: S3Bucket=s3, S3Key=s3/buckets/my-ushop-s3bucket


Invalid option specification (Namespace: 'aws:elasticbeanstalk:managedactions', OptionName: 'ManagedActionsEnabled'): Managed platform updates require
 enhanced health reporting (option SystemType in namespace aws:elasticbeanstalk:healthreporting:system).


s3 permission issue

The 403 Forbidden error typically occurs when the server understands the request made by the client, but it refuses to fulfill it due to authorization issues.
In the case of serving static files from an S3 bucket in Django, there are a few potential reasons for the 403 error:

Incorrect S3 Bucket Permissions: Make sure that the S3 bucket hosting your static files has the appropriate permissions configured.
The bucket should allow public access to the files or provide access to the specific users or roles that need to fetch the static files.
Check the bucket's permissions and ensure that they are properly set.

Incorrect IAM Role or Access Keys: If you're using AWS Identity and Access Management (IAM) to control access to your S3 bucket, verify
that the IAM role or access keys being used by your Django application have the necessary permissions to read the objects in the S3 bucket.
Ensure that the IAM role or user associated with your Django application has the required permissions to access the S3 bucket.

Incorrect S3 Bucket Configuration: Double-check the S3 bucket configuration to ensure that it is properly set up as a static file server.
Make sure that the bucket is configured to allow public access to the static files or that the necessary access policies are in place.

Incorrect URL or File Path: Check that the URL or file path used to access the static files is correct. Make sure that the URLs
in your Django templates or static file references are properly pointing to the S3 bucket.

AWS Region Mismatch: Ensure that your Django application and the S3 bucket are in the same AWS region. If they are in different regions,
 it could cause issues with accessing the static files.

CORS Configuration: If you're accessing the static files from a different domain or making cross-origin requests, make sure that
the Cross-Origin Resource Sharing (CORS) configuration is properly set on the S3 bucket to allow the necessary origins.

It's recommended to check the above points and troubleshoot accordingly based on your specific setup and requirements.


No, SECRET_KEY and AWS_ACCESS_KEY_ID are not the same in Django.

The SECRET_KEY in Django is a unique and confidential value used for cryptographic signing and securing various aspects of a Django application, such as sessions, CSRF protection, and password hashing. It is an essential security measure to keep the SECRET_KEY secret and not share it publicly or include it in version control systems.

On the other hand, AWS_ACCESS_KEY_ID is a key provided by Amazon Web Services (AWS) that is used to authenticate your application when accessing AWS services, such as Amazon S3 for storing static and media files, or Amazon EC2 for deploying instances. The AWS_ACCESS_KEY_ID is associated with your AWS account and allows your application to interact with AWS resources.

Both SECRET_KEY and AWS_ACCESS_KEY_ID may be included in the .env file for convenience and security. However, it's crucial to handle them differently:

SECRET_KEY should be kept confidential and not shared publicly. It should be included in the .env file, which should be excluded from version control using appropriate techniques like adding it to the .gitignore file.

AWS_ACCESS_KEY_ID is used to authenticate your application with AWS and can be considered less sensitive than the SECRET_KEY. However, it's still important to handle it securely. You can include AWS_ACCESS_KEY_ID in the .env file, but remember not to share the .env file publicly or include it in version control.

It's a good practice to keep sensitive information, such as SECRET_KEY and AWS_ACCESS_KEY_ID, separate from your codebase and handle them securely.
