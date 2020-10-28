# [Amplify with Cognito for Login](https://docs.amplify.aws/lib/auth/getting-started/q/platform/android)

## How To:

In the project's directory in your CLI (that is already provisioned with aws) run the following line:

```
amplify add auth
```

Then follow the below fill-in for the default setup:
```
? Do you want to use the default authentication and security configuration?
    `Default configuration`
? How do you want users to be able to sign in?
    `Username`
? Do you want to configure advanced settings?
    `No, I am done.`
```

Then finish with ```amplify push```

The project's build.gradle file will now need to include the following within its dependencies:
``` Java
  implementation 'com.amplifyframework:aws-auth-cognito:1.4.1'
```

and then include the following lines of code alongside the other ```Amplify``` plugins within your project's code (likely in the MainActivity):
``` Java
Amplify.addPlugin(new AWSCognitoAuthPlugin());
```

To see if it's live and working include this code (below the Amplify.addPlugin... snippet you added from above):
``` Java
Amplify.Auth.fetchAuthSession(
        result -> Log.i("AmplifyQuickstart", result.toString()),
        error -> Log.e("AmplifyQuickstart", error.toString())
);
```

And this will set you up with the necessary bits to allow users to authenticate with a username and password.

## How to Allow Usernames and Passwords

``` Java

Amplify.Auth.signUp(
        "username",
        "Password123",
        AuthSignUpOptions.builder().userAttribute(AuthUserAttributeKey.email(), "my@email.com").build(),
        result -> Log.i("AuthQuickStart", "Result: " + result.toString()),
        error -> Log.e("AuthQuickStart", "Sign up failed", error)
);
```

That above is the default manner to create a defaultuser. It then recommends (or requires? I'm currently uncertain) an email confirmation. The below code is _only the starting point_ as it looks very barebones, not even a real visual. Or perhaps that is all done w/in the email sent.

``` Java
Amplify.Auth.confirmSignUp(
    "username",
    "the code you received via email",
    result -> Log.i("AuthQuickstart", result.isSignUpComplete() ? "Confirm signUp succeeded" : "Confirm sign up not complete"),
    error -> Log.e("AuthQuickstart", error.toString())
);
```

At which point the console should alert you: ``` Confirm signUp succeeded ```

Now with a user within and confirmed, you can allow/enable user sign in, with the following code:

``` Java
Amplify.Auth.signIn(
    "username",
    "password",
    result -> Log.i("AuthQuickstart", result.isSignInComplete() ? "Sign in succeeded" : "Sign in not complete"),
    error -> Log.e("AuthQuickstart", error.toString())
);
```

And if it works, console shall say: ``` Sign in succeeded ```

__Note:__ if you want to add MFA (multi-factor authentification) there is much more to be done, but it is possible. And in this day and age, it is a good option to allow.

__Note 2:__ the documentation emphasizes that the phone number be formatted as: ``` +15551234567 ```

Lastly - and this might only pertain to MFA being enabled, but likely in either case - the final step is:
``` Java
Amplify.Auth.confirmSignIn(
    "confirmation code received via SMS",
    result -> Log.i("AuthQuickstart", result.toString()),
    error -> Log.e("AuthQuickstart", error.toString())
);
```
and you now have a logged in user. Or, at least the background work. I get the feeling it's up to the user to actually visually enable the auth(entification) capabilities. Likely using Handler (for the threads that amplify create/utilize).
