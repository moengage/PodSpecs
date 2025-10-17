# MoEngage Private CocoaPods Specs

This repository serves as a private CocoaPod specs host for MoEngage pods.

## Overview

This is a private spec repository that contains podspec files for MoEngage's internal and proprietary pods. It allows MoEngage to distribute and manage its CocoaPods independently from the public CocoaPods trunk.

## Adding This Specs Repository

To use pods from this private specs repository, you need to add it to your CocoaPods installation.

### Option 1: Command Line

```bash
pod repo add moengage-specs https://github.com/moengage/PodSpecs.git
```

### Option 2: In Your Podfile

Add the following line at the top of your `Podfile`:

```ruby
source 'https://github.com/moengage/PodSpecs.git'
source 'https://github.com/CocoaPods/Specs.git'
```

**Note:** When using private specs repositories, you must explicitly include the public CocoaPods specs repository as well.

## Using MoEngage Pods

Once you've added this specs repository, you can use MoEngage pods in your `Podfile` just like any other pod:

```ruby
source 'https://github.com/moengage/PodSpecs.git'
source 'https://github.com/CocoaPods/Specs.git'

platform :ios, '13.0'

target 'YourApp' do
  use_frameworks!
  
  pod 'MoEngage-iOS-SDK', '~> 10.0.0'
  # Add other MoEngage pods as needed
end
```

Then run:

```bash
pod install
```

## Adding New Podspecs (For Maintainers)

To publish a new version of a pod to this specs repository:

1. Ensure your podspec file is valid:

   ```bash
   pod spec lint YourPod.podspec --allow-warnings --skip-import-validation
   ```

2. Push the podspec to this repository:

   ```bash
   pod repo push moengage-specs YourPod.podspec --allow-warnings --skip-import-validation --use-json
   ```

Alternatively, you can manually add the podspec:

1. Clone this repository
2. Create the appropriate directory structure: `[POD_NAME]/[VERSION]/`
3. Add your `.podspec` file
4. Commit and push the changes

## Repository Structure

```text
PodSpecs/
├── [PodName]/
│   ├── [Version1]/
│   │   └── [PodName].podspec
│   ├── [Version2]/
│   │   └── [PodName].podspec
│   └── ...
└── README.md
```

## Support

For issues or questions related to MoEngage pods, please contact the MoEngage SDK team.

## License

See [LICENSE](LICENSE) file for details.
