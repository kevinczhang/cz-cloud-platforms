# S3 Encryption

## Two ways of protecting information with S3 and encryption:

* In-transit/Client Side Encryption: Using SSL or client-side encryption

![](../../../.gitbook/assets/image%20%2829%29.png)

* At rest: Request that S3 encrypt objects for you

![](../../../.gitbook/assets/image%20%2830%29.png)

## In-Transit Encryption for S3

### Using a Client-side Master Key 

* Master keys and unencrypted data are never sent to AWS 
* On upload: 
  * \(1\) The S3 client generates a random data key 
  * \(2\) User provides a client-side master key to the Amazon S3 Encryption client and then the S3 client encrypts the random data key with the client-side master key \(CSMK\) 
  * \(3\) The S3 client encrypts your data using the data key 
  * \(4\) The S3 client uploads a material description as part of the object metadata \(x-amz-meta-x-amz-key\)
* On download: 
  * \(5\) Client downloads encrypted object along with its metadata 
  * \(6\) The metadata tells the client which master key to use to perform a decryption, then using the client-side master key, the client decrypts the data key 
  * \(7\) The data key is used to decrypt the object

Note: This process is primarily handled by the SDK.

![](../../../.gitbook/assets/image%20%2840%29.png)

![](../../../.gitbook/assets/image%20%2826%29.png)

### Using an AWS KMS-managed customer master key \(CMK\) 

* Client gets a unique encryption key for each object 
* On upload: 
  * \(1\) Client first sends a request to AWS KMS for a key 
  * \(2\) AWS KMS returns an encryption key:
    * A plaintext key used to encrypt object data
    * A ciphertext blob to upload to S3 as object metadata
  * \(3\) The plaintext key is then used to encrypt the file
  * \(4\) The client uploads the encrypted file to S3 with the ciphertext blob as object metadata
* On download: 
  * \(5\) Client downloads the encrypted object and the object metadata from S3 
  * \(6\) The client then sends that ciphertext blob to AWS KMS to get the plain text 
  * \(7\) A plaintext key is used to decrypt the object

**Note:** Much of this process is handled by the SDKs in the background.

![](../../../.gitbook/assets/image%20%2810%29.png)

![](../../../.gitbook/assets/image%20%2834%29.png)

![](../../../.gitbook/assets/image%20%285%29.png)

![](../../../.gitbook/assets/image%20%2825%29.png)

### At Rest Encryption for S3

#### S3-Managed Keys \(SSE-S3\)

* Amazon S3 provides server side encryption before saving data to disk 
* Uses AES-256 \(Advanced Encryption Standard\) 
* Each object gets a unique key that is encrypted by a regularly-rotated master key 
* Add the x-amz-server-side-encryption request header to your upload request 
* Bucket policies can require all objects to use server-side encryption by requiring uploads to have the x-amz-server-side-encryption header with a value of "AES-256" 
* Keys handled by S3 and many details handled by the AWS SDKs:

![](../../../.gitbook/assets/image%20%2839%29.png)

#### KMS-Managed Keys \(SSE-KMS\)

* Similar to SSE-S3 
* Uses KMS-managed keys to encrypt objects 
* Allows for more permssion control over who can access 
* Allows for better auditing of access to data

#### Customer-Provided Keys \(SSE-C\)

* You manage the keys 
* S3 manages the encryption when writing to disk and decryption when accessing objects

