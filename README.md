		Keybase Email - PowerShell Wrapper
		greg . foss [at] owasp . org
        @heinzarelli
        https://keybase.io/heinzarelli
		v0.1 -- August 2015

## [About]

Keybase-Mail.ps1 is a basic wrapper for the windows command-line version of keybase.io. This allows you to send encrypted / signed email directly from the command-line via PowerShell.

![encrypted](/images/encrypted-email.png)

Please note, this requries the Windows Command-Line version of Keybase: https://keybase.io/docs/command_line

## [How To]

    Install Invoke-KeybaseMail Module (note the two dots!). Once this is installed, you can simply call the function (Invoke-KeybaseMail)...
        
        PS C:\> . .\keybase-mail.ps1

    Send Emcrypted Email
        
        PS C:\> Invoke-KeybaseMail -encrypt [recipient's keybase user name] -from from@address.com -to to@address.com -smtpServer 127.0.0.1 -subject "test" -message "test"

    Send Signed and Encrypted Email
        
        PS C:\> Invoke-KeybaseMail -encrypt [recipient's keybase user name] -sign -from from@address.com -to to@address.com -smtpServer 127.0.0.1 -subject "test" -message "test"

    Send Clear-Signed Email
        
        PS C:\> Invoke-KeybaseMail -clearSign -from from@address.com -to to@address.com -smtpServer 127.0.0.1 -subject "test" -message "test"

## [Parameter Breakdown]

    You may want to hard-code most of these parameters, so you can send mail easily without having to supply these parameters at run-time.

    Keybase Commands:

        -encrypt    :   Encrypt the message using Keybase. You will need to supply the recipient's Keybase username
        -sign       :   Sign the message using Keybase
        -clearSign  :   Send the message in clear-text with an accompanied PGP signature via Keybase
        -file       :   Attach an encrypted file to the email (coming soon...)

    Email Commands:

        -smtpServer :   Sets the remote SMTP Server that will be used to forward reports
        -to         :   Defines the email recipient. Multiple recipients can be separated by commas
        -from       :   Defines the email sender
        -subject    :   Define the email subject
        -message    :   Message body

## [License]

Copyright (c) 2015, Greg Foss
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:
* Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
* Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
* Neither the name of Greg Foss, LogRhythm, LogRhythm Labs, nor the names of any of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.
* This script is not 'forensically sound' as it will write to the target host. Please keep this in mind.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL <COPYRIGHT HOLDER> BE LIABLE FOR ANY
DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.