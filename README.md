# ProGrad-DBMS-Training
Open SSMS -> Connect -> Right Click Database -> Name DB

## Create Table

```
USE [TestDB]
GO

/****** Object:  Table [dbo].[Student_Details]    Script Date: 03-04-2023 09:26:32 ******/
SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE TABLE [dbo].[Student_Details](
	[_id] [int] NOT NULL,
	[name] [nchar](50) NOT NULL,
	[department] [nchar](10) NOT NULL,
	[dateOfBirth] [datetime] NOT NULL,
	[email] [nchar](20) NULL
) ON [PRIMARY]
GO
```
