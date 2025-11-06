# Testing Guide for Academix

## Quick Start Testing

### 1. Install Dependencies
```bash
pip install -r requirements.txt
```

### 2. Verify API Keys
Ensure your `.streamlit/secrets.toml` file has valid API keys:
- `TAVILY_API_KEY` - For web search
- `GEMINI_API_KEY` - For AI generation

### 3. Run the Application
```bash
streamlit run Academix.py
```

The app will open in your browser at `http://localhost:8501`

---

## Manual Testing Checklist

### ✅ Feature 1: File Upload
**Test Steps:**
1. Navigate to "Upload Study Materials" in the sidebar
2. Upload a PDF file (test with a small PDF first)
3. Upload a text file (.txt)
4. Try uploading the same file twice (should show error)
5. Verify file appears in "Uploaded Files"

**Expected Results:**
- ✅ Files upload successfully
- ✅ Duplicate file names are rejected
- ✅ Files are stored in `uploads/` directory
- ✅ File metadata is saved to database

---

### ✅ Feature 2: Document Summarization
**Test Steps:**
1. Navigate to "Summarizer"
2. Select an uploaded document
3. Adjust summary length slider (50-500 words)
4. Click "Generate Summary"
5. Verify summary is displayed

**Expected Results:**
- ✅ Summary is generated
- ✅ Summary length matches slider setting (approximately)
- ✅ Summary contains relevant content from document

---

### ✅ Feature 3: Quiz Generation
**Test Steps:**
1. Navigate to "Create Quizzes"
2. Select a document
3. Choose difficulty level (Easy/Medium/Hard)
4. Click "Generate Quiz"
5. Answer all 5 questions
6. Click "Submit Quiz"
7. Verify score and feedback

**Expected Results:**
- ✅ Quiz generates with 5 questions
- ✅ Each question has 4 options
- ✅ Can select answers
- ✅ Score is calculated correctly
- ✅ Correct/incorrect feedback is shown

---

### ✅ Feature 4: Document Q&A (Ask Questions)
**Test Steps:**
1. Navigate to "Ask Questions"
2. Select a document
3. Ask a question related to the document
4. Verify answer is based on document content
5. Ask a question NOT in the document
6. Verify web search fallback is used
7. Test chat history (enable/disable)
8. Test "New Chat" button

**Expected Results:**
- ✅ Answers are relevant to document
- ✅ Web search activates when context is insufficient
- ✅ Chat history works when enabled
- ✅ "New Chat" clears history
- ✅ Streaming response animation works

---

### ✅ Feature 5: Notes Generation
**Test Steps:**
1. Navigate to "Notes"
2. Select a document
3. Click "Generate Notes"
4. Verify notes are displayed
5. Test "Download Notes" button

**Expected Results:**
- ✅ Notes are generated in bullet format
- ✅ Notes contain key concepts
- ✅ Download button works
- ✅ Downloaded file is readable

---

### ✅ Feature 6: File Management
**Test Steps:**
1. Navigate to "Uploaded Files"
2. Verify all uploaded files are listed
3. Check file sizes are displayed correctly
4. Delete a file
5. Verify file is removed from list and storage

**Expected Results:**
- ✅ All files are displayed
- ✅ File sizes are accurate
- ✅ Delete button works
- ✅ File is removed from database and filesystem

---

## Testing Different Scenarios

### Edge Cases to Test:
1. **Empty Database**: Test with no uploaded files
2. **Large Files**: Test with large PDF files (>10MB)
3. **Invalid Files**: Try uploading non-PDF/TXT files
4. **API Failures**: Test behavior when API keys are invalid
5. **Special Characters**: Test with filenames containing special characters
6. **Long Documents**: Test with very long documents (100+ pages)

### Error Handling:
- ✅ Invalid API keys show appropriate errors
- ✅ Missing files show warnings
- ✅ Network errors are handled gracefully
- ✅ Invalid JSON responses are caught

---

## Performance Testing

1. **Load Time**: Check app startup time
2. **Response Time**: Measure time for:
   - File upload and processing
   - Summary generation
   - Quiz generation
   - Q&A responses
3. **Memory Usage**: Monitor memory with large files
4. **Concurrent Users**: Test with multiple browser tabs

---

## Browser Compatibility

Test in:
- ✅ Chrome/Edge
- ✅ Firefox
- ✅ Safari
- ✅ Mobile browsers (if applicable)

---

## Automated Testing (Optional)

To set up automated tests, you can use:
- `pytest` for unit tests
- `pytest-streamlit` for Streamlit component testing
- `unittest` for basic functionality tests

Would you like me to create automated test files?

