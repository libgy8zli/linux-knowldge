#### create a random file with size 107474182 
head -c 107374182 </dev/urandom >myfile


#### get the attached role for current ec2 
#### you also need qr installed to parse the JSON returned from cURL

`
curl http://169.254.169.254/latest/meta-data/iam/security-credentials/your-role-name

temp_creds=$(curl http://169.254.169.254/latest/meta-data/iam/security-credentials/$(curl http://169.254.169.254/latest/meta-data/iam/security-credentials/)/ | jq -r '.AccessKeyId, .SecretAccessKey, .Token')

echo tempcreds are $temp_creds

IFS=" " readarray -t parts <<< "$temp_creds"

aws configure set aws_access_key_id "${parts[0]}"
aws configure set aws_secret_access_key "${parts[1]}"
aws configure set aws_session_token "${parts[2]}"
`
