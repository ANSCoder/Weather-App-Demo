# Weather-App-Demo

Weather-App-Demo is an weather app demo written in Swift.

## Features

- [x] XML/Soap Parsing
- [x] Alamofire library use
- [x] SWXMLHash parser use
- [x] web view

In this demo i have added XML Parsing with Yahoo XML Api and getting weather details link and show on the 
web view here.

###For Parsing i used Alamofire and for XML parsing used SWXMLHash library.

```bash
$ gem install cocoapods
```

> CocoaPods 0.39.0+ is required to build Alamofire 3.0.0+.

To integrate Alamofire and SWXMLHash into your Xcode project using CocoaPods, specify it in your `Podfile`:


```ruby
source 'https://github.com/CocoaPods/Specs.git'
platform :ios, '9.0'
use_frameworks!

pod 'Alamofire', :git => 'https://github.com/Alamofire/Alamofire'
pod 'SWXMLHash', :git => 'https://github.com/drmohundro/SWXMLHash'

```
 
Then, run the following command:

```bash
$ pod install
``` 
 
 ### Response Handling with the XML data 
 
```swift
Alamofire.request(.GET, is_URL)
            .responseJSON { response in
                    let xmls = SWXMLHash.parse(response.data!)
                    func enumerate(indexer: XMLIndexer, level: Int) {
                        for child in indexer.children {
                            let name:String? = child.element!.name
                            print("\(level) \(name)")
                            // Take Link from XML data here 
                            if name! == "link" {
                                let text = child.element!.text
                                if text?.isEmpty == false{
                                   print(text)
                                  // Finish here Process
                                  completion(result: text!)
                                }
                            }
                            enumerate(child, level: level + 1)
                        }
                    }
                enumerate(xmls, level: 0)
            }
       }
'''
## FAQ

### What's the origin of the name ANSCoder?

I am independ swift and Objective c developer working for help to other new developers. 

---

## Credits

Alamofire and SWXMLHash Libraries for make this demo.

