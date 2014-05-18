
Instructions on how to use this script can be found at 
http://walkingthestack.blogspot.com/2010/09/importing-tfs-repository-into-git.html

參數說明
--------

-TFSRepository (必要的)
The TFS repository you wish to import. Ie. $/repository. 

-GitRepository (optional)
The name you want to give the Git repository. If no parameter is supplied, the default name will 'ConvertedFromTFS'.

-WorkSpaceName (optional)
During the import a temporary TFS workspace will be created. You can specify the name you wish to use for this workspace. Default 'TFS2GIT'.

-StartingCommit (optional)
You can import a sequential range of commits. Specify the first TFS commit you want to import.
When this parameter is used, EndingCommit must also be used.

-EndingCommit (optional)
You can import a sequential range of commits. Specify the last TFS commit you want to import.
When this parameter is used, StartingCommit must also be used.

-UserMappingFile (optional)
The script can convert TFS user accounts to Git accounts. For this to work you need to specify a user mapping file.
See the content of 'usermappings.txt' for an example.


使用範例
--------

套用預設值

	TFS2GIT.ps1 $/repository

或

	TFS2GIT.ps1 -TFSRepository $/repository

指定特定版本範圍

	TFS2GIT.ps1 -TFSRepository $/repository -StartingCommit 1 -EndingCommit 100

指定使用者對應檔

	TFS2GIT.ps1 -TFSRepository $/repository -UserMappingfile filename

完整範例

	Tfs2Git.ps1 -TFSRepository $/DoggyENS -WorkspaceName DoggyENS -GitRepository DoggyENS.git -UserMappingFile .\userMappings.txt
