# php-Firebase

## Overview
This project harnesses the power of Font Awesome for its sleek iconography and leverages Firebase integrated with PHP to provide robust backend services.

## Font Awesome
Font Awesome Free 5.15.4 is used for icons. The relevant CSS file is included in the project:

```css
/*!
 * Font Awesome Free 5.15.4 by @fontawesome - https://fontawesome.com
 * License - https://fontawesome.com/license/free (Icons: CC BY 4.0, Fonts: SIL OFL 1.1, Code: MIT License)
 */
```

## Firebase Integration with PHP
The application uses Firebase for backend services such as authentication, database, and storage. Below is a brief explanation of how Firebase is integrated with PHP.

### Setup Firebase in PHP

1. **Install Firebase PHP SDK**: Use Composer to install the Firebase Admin SDK.
    ```bash
    composer require kreait/firebase-php
    ```

2. **Initialize Firebase**: Create a PHP script to initialize Firebase with your service account credentials.
    ```php
    require 'vendor/autoload.php';

    use Kreait\Firebase\Factory;
    use Kreait\Firebase\ServiceAccount;

    $serviceAccount = ServiceAccount::fromJsonFile(__DIR__.'/path/to/serviceAccountKey.json');
    $firebase = (new Factory)
        ->withServiceAccount($serviceAccount)
        ->create();
    ```

3. **Authentication**: Use Firebase Authentication for user management.
    ```php
    $auth = $firebase->getAuth();
    $user = $auth->verifyIdToken($idToken);
    ```

4. **Database**: Interact with Firebase Realtime Database.
    ```php
    $database = $firebase->getDatabase();
    $reference = $database->getReference('path/to/child');
    $snapshot = $reference->getSnapshot();
    $value = $snapshot->getValue();
    ```

5. **Storage**: Use Firebase Storage for file uploads.
    ```php
    $storage = $firebase->getStorage();
    $bucket = $storage->getBucket();
    $file = fopen('path/to/local/file', 'r');
    $bucket->upload($file, [
        'name' => 'path/in/bucket'
    ]);
    ```

## Configuration 

first you need to create a service account in the firebase console and get the json api

after that you can add chage the path to the service account key in the php script admin.html adn all-product.html

json firebase api key in the file

```php
import { initializeApp } from 'https://www.gstatic.com/firebasejs/9.2.0/firebase-app.js';
import { getFirestore, collection, getDocs, addDoc, updateDoc, deleteDoc, doc } from 'https://www.gstatic.com/firebasejs/9.2.0/firebase-firestore.js';

// Your web app's Firebase configuration
const firebaseConfig = {
    apiKey: "AIBMLafGU",
    authDomain: "pr.firebaseapp.com",
    projectId: "pr",
    storageBucket: "pro.appspot.com",
    messagingSenderId: "617148",
    appId: "1:61148:web:49dd61",
    measurementId: "G-5YVB"
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
const db = getFirestore(app);
```



## Conclusion
This project integrates Font Awesome for icons and Firebase for backend services using PHP. The Firebase PHP SDK is used to handle authentication, database interactions, and file storage.
