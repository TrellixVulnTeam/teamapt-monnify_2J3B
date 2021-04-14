                                  MONNIFY PYTHON LIBRARY USER GUIDE
                                            Version 1.0.0

Monnify is one of the products of TeamApt <https://www.teamapt.com/> . Monnify empowers businesses in the formal & informal sectors with the right tools & solutions to manage their finances and grow their businesses. Businesses in the formal economy benefit from our payment infrastructure that simplifies how they accept, manage and make payments. While smaller-scale businesses and entrepreneurs benefit from our market-community focused products that give them accessible, affordable and convenient short term working capital.

                                  MONNIFY PYTHON LIBRARY USER GUIDE

Before you can start integrating to Monnify, you will need to sign up on Monnify. Click <https://app.monnify.com/create-account> to sign up. After successful registration, login and for your credentials. 

                                            CREDENTIAL NEEDED

1. API KEY
2. SECRET KEY
3. CONTRACT
4. WALLET ID

All this can be seen on the setting area when you login to you logged in.


                                            HOW TO USE THE LIBRARY
To use the library, we have to use package installer (pip) by running: pip install teamapt-monnify

After successfull installation, we can now use the package in our development by importing it in our script


            from monnify.monnify import monnifyCredential, get_token, Monnify

            monnify = Monnify()

            api_key = "MK_TEST_8UBXGKTYYYWB"
            secret_key = "ENRC4FDYYYETKA53YPXBFLUFXWYHG2"
            contractCode = '2917634883'
            walletId = '654CAB211YY36760A659C787B2AA38E8'

            merchant_credential = monnifyCredential(api_key, secret_key, contractCode, walletId, is_live=False)

            NOTE: If you are in sandbox please is_live = False and can only be set to True when you are in 
                  production and make sure you change credentials to live credentials

            token = get_token(merchant_credential)



          1.VERIFY BANK ACCOUNT

            bank = monnify.verify_account(merchant_credential, accountNumber='2213324087', bankCode='057')
            print(bank)

            {
              'requestSuccessful': True, 
              'responseMessage': 'success', 
              'responseCode': '0', 
              'responseBody': {
                'accountNumber': '2213324087', 
                'accountName': 'SAMSON   ILEMOBAYO', 
                'bankCode': '057'
              }
            }
          
          2 CREATE INVOICE

            create_invoice = reserve.create_invoice(login_credential, amount='1000', invoiceReference='uueyyws', description='test invoice', 
            customerEmail='test@gmail.com', customerName='Samson', expiryDate='2021-04-30 12:00:00', paymentMethods=['CARD', 'ACCOUNT_TRANSFER'], redirectUrl='http://abc.com')
            print(create_invoice)

            {
              'requestSuccessful': True, 
              'responseMessage': 'success', 
              'responseCode': '0', 
              'responseBody': {
                'amount': 1000, 
                'invoiceReference': 'uueyyws', 
                'invoiceStatus': 'PENDING', 
                'description': 'test invoice', 
                'contractCode': '2917634883', 
                'customerEmail': 'test@gmail.com', 
                'customerName': 'Samson', 
                'expiryDate': '2021-04-30 12:00:00', 
                'createdBy': 'MK_TEST_8UBXGKTFSB', 
                'createdOn': '2021-04-14 15:18:31', 
                'checkoutUrl': 'https://sandbox.sdk.monnify.com/checkout/MNFY|63|20210414151813|000197', 
                'accountNumber': '3000041788', 
                'accountName': 'tes', 
                'bankName': 'Wema bank', 
                'bankCode': '035', 
                'redirectUrl': 'http://abc.com'
              }
            }






