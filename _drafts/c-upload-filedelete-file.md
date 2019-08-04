---
layout: post_layout
title: 'C# Upload File/Delete File'
date: 2019-05-25 07:40:00
location: Auckland
pulished: true
excerpt_separator: '```'
---

These days, i have created some restful api based on uploading someone's information including upload file or delete file from the cloud. So, i gonna share my method to upload or delete file from directory.
{: .present-before-paste}

```c#
protected UploadFileModel UploadFile(IFormFile file,string folderName, int id,string strDateTime)
        {
            var model = new UploadFileModel();
            try
            {
                string currentFileExtension = Path.GetExtension(file.FileName);
                var saveName = id.ToString() + strDateTime + currentFileExtension;
                var newPath = Path.Combine("images", folderName, saveName);
                var path = Path.Combine(Directory.GetCurrentDirectory(), "wwwroot", newPath);
                using (var stream = new FileStream(path, FileMode.Create))
                {
                    file.CopyTo(stream);
                }
                
                model.IsUploadSuccess = true;
                model.ErrorMessage = "";
                return model;
            }
            catch (Exception ex)
            {
                model.IsUploadSuccess = false;
                model.ErrorMessage = ex.Message;
                return model;
            }
        }
```

```c#
protected void DeleteFile(string filePath)
        {
            var folderName = Path.Combine("wwwroot", filePath);
            if (System.IO.File.Exists(folderName))
            {
                System.IO.File.Delete(folderName);
            }
            else
            {
                throw new Exception("Delete Fail");
            }
        }
```
