# google-authenticator-codeigniter
setup two step verification with codeigniter And google authenticator 

Usage:
// load library

$this->load->library('GoogleAuthenticator');


		// generates the secret code
		$secret_code = $this->googleauthenticator->createSecret();

		// generates the QR code for the link the user's phone with the service
		$qr_code_url = $this->googleauthenticator->getQRCodeGoogleUrl('Mohsen', 'info@mohseng.ir', $secret_code);

		// also, you can get a code to test the service
		$one_code_with_app = $this->googleauthenticator->getCode($secret_code);

		// get the user's phone code and the secret code that was generated, and verify
		$checkResult = $this->googleauthenticator->verifyCode($secret_code, $one_code_with_app, 2); // 2 = 2*30sec clock tolerance

		if ($checkResult) {
			echo 'OK';
		} else {
			echo 'FAILED';
		}
