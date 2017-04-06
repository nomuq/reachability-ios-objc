# Check-Internet-Reachability-iOS-Objective-C
Check Internet Reachability iOS Objective C
    
    
    #import "AppDelegate.h"
    #import "Reachability.h"
    @interface AppDelegate ()

    @end

    @implementation AppDelegate


    - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // Override point for customization after application launch.
    Reachability* reach = [Reachability reachabilityWithHostname:@"www.google.com"];
    
    // Set the blocks
    reach.reachableBlock = ^(Reachability*reach)
    {
        
        dispatch_async(dispatch_get_main_queue(), ^{
            NSLog(@"REACHABLE!");
            
        });
    };
    
    reach.unreachableBlock = ^(Reachability*reach)
    {
        NSLog(@"UNREACHABLE!");
        
        [[[UIAlertView alloc] initWithTitle:@"No Internet Connection" message:nil delegate:nil cancelButtonTitle:@"OK" otherButtonTitles:nil]show] ;
        
  
    };
    
    // Start the notifier, which will cause the reachability object to retain itself!
    [reach startNotifier];
    
    return YES;
    }

