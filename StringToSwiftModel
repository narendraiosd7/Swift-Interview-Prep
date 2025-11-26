import Foundation

/**
 * Student Marks Parser
 *
 * This program parses a JSON string containing student information and extracts
 * the marks for each student based on their roll number. It demonstrates:
 * - JSON parsing with Codable protocol
 * - Optional property handling
 * - Dictionary creation from parsed data
 */

/// Sample JSON data containing student information
/// Note: Some students may not have marks, and duplicate roll numbers will overwrite previous entries
let jsonString = """
 [
   {
     "name":"a",
     "age": 12,
     "roll": 1,
     "marks": 76
   },
   {
     "name":"b",
     "age": 12,
     "roll": 2,
     "marks": 35
   },
   {
     "name":"c",
     "age": 12,
     "roll": 3
   },
   {
     "name":"b",
     "age": 12,
     "roll": 2,
     "marks": 45
   }
 ]
"""

/**
 * Student data structure that conforms to Codable protocol for JSON parsing
 *
 * Properties:
 * - name: The student's name (required)
 * - age: The student's age (required)
 * - roll: The student's roll number, used as unique identifier (required)
 * - marks: The student's marks, may be nil if not provided in JSON (optional)
 */
struct Student: Codable {
  let name: String
  let age: Int
  let roll: Int
  let marks: Int?
}

/// Dictionary to store student marks with roll number as key and marks as value
/// Key: Roll number (Int), Value: Marks (Int) - nil marks are not stored
var studentMarks: [Int: Int] = [:]

// JSON Parsing and Processing
// Convert the JSON string to Data object for parsing
if let jsonData = jsonString.data(using: .utf8) {
  do {
    // Decode JSON array into Student objects using JSONDecoder
    let students = try JSONDecoder().decode([Student].self, from: jsonData)
    
    // Process each student and extract marks
    // Note: If a roll number appears multiple times, the last occurrence will overwrite previous values
    for student in students {
      // Only store marks if they exist (not nil)
      studentMarks[student.roll] = student.marks
    }
  } catch {
    // Handle JSON parsing errors gracefully
    print("Error decoding JSON: \(error)")
  }
}

// Display the final dictionary containing roll numbers mapped to marks
// Expected output: [1: Optional(76), 2: Optional(45), 3: nil]
print(studentMarks)

