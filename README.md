# AssertYourself
iOS Unit Testing by Example - Chapter 1

![image](https://user-images.githubusercontent.com/47273077/178744829-44543765-d038-4d50-938d-7fb790badb98.png)


```swift

import XCTest
@testable import AssertYourself

class AssertYourselfTests: XCTestCase {
    
    func test_fail() {
        XCTFail("We have a problem")
        // failed - We have a problem
    }
    
    func test_fail_withInterpolatedMessage() {
        let theAnswer = 42
        XCTFail("The Answer to the Great Querstion is \(theAnswer)")
        // failed - The Answer to the Great Querstion is 42
    }
    
    func test_assertNil() {
        let optionalValue: Int? = 123
        XCTAssertNil(optionalValue)
        // XCTAssertNil failed: "123"
    }
    
    struct SimpleStruct {
        let x: Int
        let y: Int
    }
    
    func test_assertNul_withSimpleStruct() {
        let optionalValue: SimpleStruct? = SimpleStruct(x: 1, y: 2)
        XCTAssertNil(optionalValue)
        // XCTAssertNil failed: "SimpleStruct(x: 1, y: 2)"
    }
    
    struct StructWithDescription: CustomStringConvertible {
        let x: Int
        let y: Int
        
        var description: String { "\(x), \(y)" }
    }
    
    func test_assertNil_wtihSelfDescribingType() {
        let optionalValue: StructWithDescription? = StructWithDescription(x: 1, y: 2)
        XCTAssertNil(optionalValue)
        // XCTAssertNil failed: "1, 2"
    }
    
    func test_assertEqual() {
        let actual = "actual"
        XCTAssertEqual(actual, "expected")
        // XCTAssertEqual failed: ("actual") is not equal to ("expected")
    }

    func test_assertEqual_withOptional() {
        let result: String? = "foo"
        XCTAssertEqual(result, "bar")
        // XCTAssertEqual failed: ("Optional("foo")") is not equal to ("Optional("bar")")
    }
    
    func test_floatingPointDanger() {
        let result = 0.1 + 0.2
        XCTAssertEqual(result, 0.3)
        // XCTAssertEqual failed: ("0.30000000000000004") is not equal to ("0.3")
    }
    
    func test_floatingPointFixed() {
        let result = 0.1 + 0.2
        XCTAssertEqual(result, 0.3, accuracy: 0.0001)
    }
    
    func test_messsageOverkill() {
        let actual = "actual"
        XCTAssertEqual(actual, "expected", "Expected \"expected\" but got \(actual)\"")
        // XCTAssertEqual failed: ("actual") is not equal to ("expected") - Expected "expected" but got actual"
    }
}

```
