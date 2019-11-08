pipeline {
	
	agent any

    environment {
        ARM_SUBSCRIPTION_ID='d554009c-8c0b-44c0-afaa-4b7e3878bf0e'
        ARM_CLIENT_ID='644ab028-ae15-4e1f-a19a-8d2e547b6437'
        ARM_CLIENT_SECRET='4e548205-ac90-4124-8b75-0b8c860e3fdc'
        ARM_TENANT_ID='50640584-2a40-4216-a84b-9b3ee0f3f6cf'
        ARM_ENVIRONMENT='public'
    }

	stages {

		stage('create resource') {

			steps {
				dir('ResourceGroup') {
					sh 'ls'
					sh 'terraform init'
					sh 'terraform plan'
					sh 'terraform apply -auto-approve'
					sh 'env'
				}
			}
		}

        stage('terraform init') {

			steps {
				dir('TerraformLAB') {
					sh 'terraform init'
					sh "terraform plan -var 'admin_password=CONU2019@LAB' -var 'location=eastus'"
					sh "terraform apply -auto-approve -var 'location=eastus' -var 'admin_password=CONU2019@LAB'"
				}
			}
		}
	}
}