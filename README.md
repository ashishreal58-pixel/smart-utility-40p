/**
 * calculator.js
 * -------------------
 * CLI-Based Calculator using process.argv
 *
 * Usage:
 *   node calculator.js <operation> <num1> <num2>
 *
 * Examples:
 *   node calculator.js add 10 5
 *   node calculator.js sub 10 5
 *   node calculator.js mul 10 5
 *   node calculator.js div 10 5
 */

// process.argv[0] -> path to node
// process.argv[1] -> path to this script
// process.argv[2] -> operation (add/sub/mul/div)
// process.argv[3], process.argv[4] -> the two numbers
const args = process.argv.slice(2);
const [operation, rawA, rawB] = args;

// Handle missing arguments gracefully
if (!operation || rawA === undefined || rawB === undefined) {
  console.log("Error: Missing arguments.");
  console.log("Usage: node calculator.js <add|sub|mul|div> <num1> <num2>");
  process.exit(1);
}

const a = Number(rawA);
const b = Number(rawB);

// Handle invalid numbers gracefully
if (Number.isNaN(a) || Number.isNaN(b)) {
  console.log("Error: Both num1 and num2 must be valid numbers.");
  process.exit(1);
}

let result;

switch (operation.toLowerCase()) {
  case "add":
    result = a + b;
    console.log(`Result: ${result}`);
    break;

  case "sub":
    result = a - b;
    console.log(`Result: ${result}`);
    break;

  case "mul":
    result = a * b;
    console.log(`Result: ${result}`);
    break;

  case "div":
    if (b === 0) {
      console.log("Error: Division by zero is not allowed.");
      process.exit(1);
    }
    result = a / b;
    console.log(`Result: ${result}`);
    break;
