---
name: yila-files
description: Upload papers, figures or data to Yila. Use when a Yila tool needs a file the user has locally (a paper PDF, a reference image, a paywalled article) or returns NEEDS_UPLOAD.
---

# Upload files to Yila

1. Call `yila_upload_file` with the file name, size and type. It returns an upload URL and headers, valid for a short time.
2. Upload the bytes with an HTTP PUT to that URL, sending exactly the returned headers (for example with `curl -T`). Do not paste file contents into a tool call.
3. Call `yila_upload_file` again with the upload id to finish. It returns a `file_id`.
4. Pass the `file_id` to the tool that needed it (`yila_figure_create`, `yila_read_papers`).

Limits: one file up to 50 MB. Upload only files the user gave you or asked you to send; uploading is sending the user's data to Yila.

If the host cannot upload files (no shell or network access), tell the user to drag the file into their Yila project in the browser, then continue with the paper's cite key.
