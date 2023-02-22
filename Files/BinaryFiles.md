---
title: BinaryFiles
description: 
published: true
date: 2022-10-28T23:47:56.519Z
tags: 
editor: markdown
dateCreated: 2022-10-28T19:00:53.710Z
---

### Binary files {#binary-files .unnumbered}

A binary file is ultimately just a sequence of 0s and 1s (as are all files). A binary file is created when the software (and the programmer) specifies a specific layout for the sequence of 0s and 1s. Data is written according to that specific layout, and then it can be read back in again using the same rules for layout. The rules for file organization of binary files are set by the software (ultimately by the programmer) that created the file, which results in proprietary file formats that can only be read by applications designed to read those specific files.

You've likely had lots of experience with binary files since most gamesave files, word processor documents and media files are some form ofbinary format.

From a programming perspective, binary files are much easier to workwith when the size of each record in the file is fixed. Consider a program that stores the contents of a music library to a file on disk.

Each record in the music library is written to the binary file in such a way that the records can be read back one at a time. If we know that each record is exactly the same length, then it is very easy to traverse the file looking for the nth record.

One side effect of this is that when you are storing string in a binary file, it is easier to use statically allocated strings so that all records are the same size.

-   In C, fopen opens any kind of file and gives you a file pointer

-   fseek can be used to find a position in any kind of file, but makes
    the most sense when you know exactly how long each record is

-   rewind can be used to reset the file pointer to the beginning of the
    file

-   fgets, fscanf, and fprintf are the tools for reading and writing
    text files. They work because text files are in an agreed upon
    format

-   fread and fwrite are the tools for reading and writing binary files

fseek makes use of three constants that are predefined. `SEEK_SET`, `SEEK_CUR`, and `SEEK_END`. `SEEK_SET` is predefined to be the beginning of the file, `SEEK_END` is predictably the end of the file, and `SEEK_CUR` is the current position of the file. `SEEK_CUR` changes each time fseek,fread, or rewind are called. The syntax for fseek is `fseek(filePtr,howFarToMove, whereToStart)` The address in the file pointer is changed as a result of calling fseek.

![image](/img/fseek.jpg) []{#fseek label="fseek"}

The listing below gives an example program for reading and writing to binary files. Notice that the call to fopen uses either `"wb"` or "`rb"` to read and write a binary file as opposed to a text file. The struct used in this example is described in more detail in subsequent sections of this ebook.

    #include<stdio.h>
    #include<stdlib.h>
        
    struct musicRecord {
      char artist[15];
      char title[25];
      int minutesLong;
      int secondsLong;
      char *genre;
    };

    int main()
    {
      int i;
      FILE *filePtr;
      struct musicRecord * myRecord;
     struct musicRecord * myReadingRecord;
      myRecord = malloc(sizeof(struct musicRecord));

      /*write a file */
      filePtr=fopen("test.bin","wb");
      if (filePtr==NULL)
        {
          printf("Unable to open file!");
          return 1;
        }
      for (i=1; i <= 10; i++)
        {
          myRecord->minutesLong= i*i;
          fwrite(myRecord, sizeof(struct musicRecord), 1, filePtr); /*location, size, number, file*/
        }
      fclose(filePtr);
      free(myRecord);

      /*read from the file */
     myReadingRecord = malloc(sizeof(struct musicRecord));
      filePtr=fopen("test.bin","rb");
      if (filePtr==NULL)
        {
          printf("Unable to open file!");
          return 1;
        }
      for (i=1; i <= 10; i++)
        {
         fread(myReadingRecord, sizeof(struct musicRecord), 1, filePtr); /*location, size, number, file*/
         printf("The number is: %d\n", myReadingRecord->minutesLong);
        }
      fclose(filePtr);
      free(myReadingRecord);

      /*find the 4th record in the file */
     myReadingRecord = malloc(sizeof(struct musicRecord));
      filePtr=fopen("test.bin","rb");
      if (filePtr==NULL)
        {
          printf("Unable to open file!");
          return 1;
        }
      fseek(filePtr,sizeof(struct musicRecord)*3,SEEK_SET);
      // printf("%ld\n", ftell(filePtr));
      fread(myReadingRecord,sizeof(struct musicRecord),1,filePtr);
      printf("The number of the fourth record is: %d\n", myReadingRecord->minutesLong);
      fclose(filePtr);
      return 0;
    }
