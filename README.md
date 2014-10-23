# TPCocoaGPG

Objective-C wrapper around GPG.

This library aims to be a simple, easy to use library to deal with GPG. It does
not try to be complete, nor to get rid of the GPG binary.


## Installation

The recommended way to install this library is CocoaPods:

pod 'TPCocoaGPG', :git => 'https://github.com/pelletier/TPCocoaGPG.git', :branch => :master


## Usage

See [TPCocoaGPG.h](TPCocoaGPG/TPCocoaGPG.h) for the full API. See
[TPCocoaGPGSpecs.m](TPCocoaGPGTests/TPCocoaGPGSpecs.m) for usage examples.

### Initialization

```objc
#import <TPCocoaGPG.h>
TPCocoaGPG* gpg = [[TPCocoaGPG] initGpgPath:@"/usr/local/bin/gpg" andHome:@"/tmp"];
```

### List keys

```objc
NSArray* keys = [gpg listPublicKeys];
NSArray* keys = [gpg listSecretKeys];
```

### Load key by fingerprint

```objc
TPGPGKey* key = [gpg getPublicKeyWithFingerprint:@"F2479DE6CFB6B695"];
TPGPGKey* key = [gpg getSecretKeyWithFingerprint:@"F2479DE6CFB6B695"];
```

### Encrypt

```objc
NSData* encrypted = [gpg encryptData:data withKey:key andPassphrase:@"pass"];
NSData* encrypted = [gpg encryptData:data withKey:key];
```

### Decrypt

```objc
NSData* decrypted = [gpg decryptData:data withKey:key andPassphrase:@"pass"];
NSData* decrypted = [gpg decryptData:data withKey:key];
```

### Check if a passphrase unlocks a key

```objc
BOOL unlocks = [gpg checkIfPassphrase:@"pass" unlocksKey:key];
```

### Import a key into the keyring

```objc
[gpg importIntoKeyring:key];
```


## Development

Install development dependencies: `pod install`.
Open the workspace and run the tests.


## License

MIT. See LICENSE.
