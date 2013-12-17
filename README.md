# AFOAuth2Client

AFOAuth2Client is an extension for [AFNetworking 2.0](http://github.com/AFNetworking/AFNetworking/) that greatly simplifies the process of authenticating against an [OAuth 2](http://oauth.net/2/) provider.
This is a fork from [AFNetworking / AFOAuth2Client](http://github.com/AFNetworking/AFOAuth2Client) which has some additions for my own use like AFHTTPRequestOperation error response, expiration handling and small fixes

## Example Usage

``` objective-c
NSURL *url = [NSURL URLWithString:@"http://example.com/"];
AFOAuth2Client *oauthClient = [AFOAuth2Client clientWithBaseURL:url clientID:kClientID secret:kClientSecret];

[oauthClient authenticateUsingOAuthWithURLString:[NSString stringWithFormat:@"%@/oauth/v2/token",[[[NSBundle mainBundle] infoDictionary]objectForKey:@"BaseURL"]] 
									username:@"username" 
									password:@"password" 
									scope:@"scope" 
									success:^(AFOAuthCredential *credential) {
                                        NSLog(@"I have a token! %@", credential.accessToken);
                                        [AFOAuthCredential storeCredential:credential withIdentifier:oauthClient.serviceProviderIdentifier];
                                    }
                                    failure:^(AFHTTPRequestOperation *operation, NSError *error) {
                                        NSLog(@"Error: %@", error);
                                    }];
```

## Contact AFOAuth2Client 0.2

- http://github.com/wbroek
- http://twitter.com/wbroek

## Contact AFNetworking 2.0

Mattt Thompson

- http://github.com/mattt
- http://twitter.com/mattt
- m@mattt.me

## License

AFOAuth2Client is available under the MIT license. See the LICENSE file for more info.
