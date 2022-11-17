M3/
Data transfer OUT to the internet has tiered pricing per GB. 
Data transfer OUT to other AWS services has a cost per GB.

AWS Snowball is good for transfering dozens of TB to PB (petabytes) of data to AWS. Local data transfer to a Snowball device is faster than transfering directly to S3 over the internet. Transfer time to AWS depends on physical package shipping times.

When using multipart uploads, an upload failure requires a restart of only failed part uploads instead of restarting the entire file upload. This method provides a better solution for unreliable connections.



