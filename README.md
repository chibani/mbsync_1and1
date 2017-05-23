# Sample config for mbsync

For 1&1 users, to migrate a "Basic Email" account to an Exchange 2013 account.

1&1, at the time this is written, doesn't allow to simply upgrade from a Basic or Pro Email account to and Exchange account (don't know why, but still...).  
Also, you can't create an Exchange account with an existing email address.

So, during the migration, you need to :
 - Download all the emails from the existing (Basic or Pro) account
 - Delete the existing (Basic or Pro) account
 - Create the Exchange account
 - Wait for its credentials to be usable (aka able to connect via IMAP)
 - Upload the downloaded emails to the freshly created Exchange account

## Installation
This config file is aimed to be used with [mbsync](http://isync.sourceforge.net/mbsync.html).  
On MacOS, you can install it with brew: ``brew install isync``.  
On Debian or Ubuntu (or any other Linux distro), I think you can use apt or your package management tool.

## Usage
In order to migrate the account, you need to :

 - Copy the ``sample`` directory, and rename the copy (the way you want).
 - Create a ``mails`` directory (simple ``mkdir mails`` will do the job).  
 - Edit the ``mbsync_config`` file, changing the accounts logins and passwords.  
 - Download emails from original IMAP account : ``mbsync -c ./mbsync_config download``.  
 - When it's done, launch ``sh cleanup.sh`` (it will rename the synced files properly).  
 - If you want the same email address, it's now you will delete the Basic Account and create the Exchange account
 - Then, you can "upload" the mails to the destination IMAP account : ``mbsync -c ./mbsync_config upload``
 - You're done !

During the upload execution, you can connect to your Exchange account and see the emails being sent.
