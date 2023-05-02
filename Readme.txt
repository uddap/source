pip install -r requirements.txt --upgrade



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
ERROR: InvalidParameterValueError - "Error making request to CodeCommit: Could not retrieve 30b2a0e3701244c667ef0c3e01004863f7fb63d6 (Service: AWSCodeCommit; Status Code: 400; Error Code: CommitIdDoesNotExistException; Request ID: 6a435ff7-25a3-444b-90cb-3b1804ad51db; Proxy: null)"

SOLUTION-
