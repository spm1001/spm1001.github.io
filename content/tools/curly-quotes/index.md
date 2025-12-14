---
title: "Curly Quotes Converter"
date: 2024-12-14
description: "Convert straight quotes to typographic curly quotes"
slug: "curly-quotes"
---

Convert straight quotes to typographic curly quotes (" " becomes " " and ' ' becomes ' ').

<div class="tool-container">
<textarea id="input" placeholder="Paste your text here..." style="width: 100%; height: 200px; padding: 1rem; font-size: 1rem; border: 2px solid var(--card-border-color); border-radius: 8px; resize: vertical; background: var(--card-background); color: var(--body-text-color);"></textarea>

<div style="margin: 1rem 0; display: flex; gap: 0.5rem; flex-wrap: wrap;">
<button onclick="convert()" style="padding: 0.75rem 1.5rem; font-size: 1rem; border: none; border-radius: 6px; cursor: pointer; background: var(--accent-color); color: white;">Convert</button>
<button onclick="copyOutput()" style="padding: 0.75rem 1.5rem; font-size: 1rem; border: none; border-radius: 6px; cursor: pointer; background: var(--card-background); color: var(--body-text-color); border: 1px solid var(--card-border-color);">Copy Result</button>
<button onclick="clearAll()" style="padding: 0.75rem 1.5rem; font-size: 1rem; border: none; border-radius: 6px; cursor: pointer; background: var(--card-background); color: var(--body-text-color); border: 1px solid var(--card-border-color);">Clear</button>
</div>

<div id="output" style="background: var(--code-background-color); padding: 1rem; border-radius: 8px; white-space: pre-wrap; font-family: inherit; min-height: 100px;"></div>
</div>

## What it converts

- `"` becomes opening or closing double quote (" ")
- `'` becomes opening or closing single quote / apostrophe (' ')

The converter is smart about context - it tracks whether you're inside a quote and handles apostrophes in contractions (like "don't") correctly.

<script>
var OPEN_DOUBLE = "\u201C";
var CLOSE_DOUBLE = "\u201D";
var OPEN_SINGLE = "\u2018";
var CLOSE_SINGLE = "\u2019";

function convertQuotes(text) {
  var result = "";
  var inDoubleQuote = false;
  var inSingleQuote = false;

  for (var i = 0; i < text.length; i++) {
    var char = text[i];
    var prevChar = i > 0 ? text[i - 1] : "";
    var nextChar = i < text.length - 1 ? text[i + 1] : "";

    if (char === '"') {
      if (inDoubleQuote) {
        result += CLOSE_DOUBLE;
        inDoubleQuote = false;
      } else {
        result += OPEN_DOUBLE;
        inDoubleQuote = true;
      }
    } else if (char === "'") {
      var isApostrophe = /[a-zA-Z]/.test(prevChar) && /[a-zA-Z]/.test(nextChar);
      if (isApostrophe) {
        result += CLOSE_SINGLE;
      } else if (inSingleQuote) {
        result += CLOSE_SINGLE;
        inSingleQuote = false;
      } else {
        if (/[a-zA-Z0-9]/.test(nextChar)) {
          result += OPEN_SINGLE;
          inSingleQuote = true;
        } else {
          result += CLOSE_SINGLE;
        }
      }
    } else {
      result += char;
    }
  }
  return result;
}

function convert() {
  var input = document.getElementById("input").value;
  var output = convertQuotes(input);
  document.getElementById("output").textContent = output;
}

function copyOutput() {
  var output = document.getElementById("output").textContent;
  navigator.clipboard.writeText(output).then(function() {
    alert("Copied to clipboard!");
  });
}

function clearAll() {
  document.getElementById("input").value = "";
  document.getElementById("output").textContent = "";
}
</script>
