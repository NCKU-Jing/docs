Cryptomator
====

:::{toctree}
:hidden:
:titlesonly:

architecture/index.md
:::

:::{image} _images/cryptomator.png
:alt: Cryptomator
:width: 400px
:::

Support for client-side encryption with [Cryptomator](https://cryptomator.org/) interoperable vaults to secure your data on any server or cloud storage.

:::{image} _images/Browse_Cryptomator_Vault.gif
:alt: Browse Cryptomator Vault
:width: 600px
:::

The client-side encryption feature in Cyberduck and Mountain Duck is based on the excellent concepts and work of [Cryptomator](https://cryptomator.org/). Cryptomator is free and open-source software. Since Cyberduck is also open-source software anyone is able to audit the source code. That means no security by obscurity, no hidden backdoors from third parties, no need to trust anyone except yourself.

:::{tip}
Compared to other client-side-encryption solutions, the Cryptomator based approach yields a few crucial advantages:
- In addition to file content encryption, file and directory names are encrypted and directory structures obfuscated.
- No online services, no subscriptions, no accounts.
- No need to share your cloud storage provider credentials.
:::

## Create new Vault

You can create a new vault directory anywhere on your remote storage. This will initialize the vault with a `masterkey.cryptomator`. A backup of the master key file (`masterkey.cryptomator`) is saved in user defaults. The encrypted keys in `masterkey.cryptomator` are not more sensitive than the encrypted files in the vault. For technical aspects, refer to [Masterkey Derivation](https://docs.cryptomator.org/en/latest/security/architecture/#masterkey-derivation).

:::::{tabs}
::::{group-tab} Cyberduck

Choose *File → New Vault…* to create a new vault. 

:::{image} _images/New_Encrypted_Vault_File_Menu_Option.png
:alt: New Encrypted Vault File Menu Option
:width: 600px
:::

::::
::::{group-tab} Mountain Duck

1. Choose *New Vault…* from the Finder Extension toolbar or context menu using right-click in Finder or Windows Explorer.

    :::{image} _images/Mountain_Duck_Create_New_Vault_Windows_Explorer.png
    :alt: Mountain Duck Create New Vault (Windows Explorer)
    :width: 400px
    :::

1. Choose a name for the Vault folder and a passphrase to secure the Vault.

    :::{image} _images/Create_New_Vault.png
    :alt: Create New Vault
    :width: 400px
    :::

::::
:::::

## Unlock Vault

### Discovery

When _Preferences → Cryptomator → Auto detect and open vault in browser_ is enabled, opening a directory in the browser that is a Cryptomator Vault, a prompt is displayed to unlock the vault using the provided passphrase and decrypt the directory and filenames. If you cancel the prompt, the encrypted vault content is displayed.

:::{note}
A vault is only detected if `masterkey.cryptomator` or `vault.cryptomator` are found as one of the 10 files of the directory listing retrieved from the server.
:::

:::::{tabs}
::::{group-tab} macOS

:::{image} _images/Mountain_Duck_Unlock_Vault.png
:alt: Mountain Duck Unlock Vault
:width: 400px
:::

::::
::::{group-tab} Windows

:::{image} _images/Mountain_Duck_Unlock_Vault_Windows.png
:alt: Mountain Duck Unlock Vault (Windows)
:width: 400px
:::

::::
:::::

### Manual

::::{tabs}
:::{group-tab} Cyberduck

Choose the *Cryptomator* button in the toolbar or *File → Unlock Vault* and *File →Lock Vault* menu to unlock or lock a vault respectively.

:::
:::{group-tab} Mountain Duck

Lock and unlock vaults within the Finder or Windows Explorer using the context menu:

 * *Mountain Duck → Cryptomator → Lock Vault*
 * *Mountain Duck → Cryptomator → Unlock Vault*

:::
::::

:::{attention}
The menu option is disabled if you have set Preferences → Cryptomator → Auto detect and open vault in browser
:::

### Save Passphrase

You can check *Add to Keychain* to save the passphrase to open the vault with the master key file in your login keychain. The checkbox is disabled by default. 

:::::{tabs}
::::{group-tab} macOS

Manage your passwords with *Keychain Access.app* on Mac. Refer to the [Keychain Access User Guide](https://support.apple.com/kb/PH20093?locale=en_US). Another application that wants to access the vault passphrase from the login keychain will trigger a permission prompt.

:::{image} _images/Keychain_Access_Cryptomator_Passphrase.png
:alt: Keychain Access Cryptomator Passphrase
:width: 400px
:::

::::
::::{group-tab} Windows

Passwords are saved in the *Credential Manager*. You can view and delete your saved login information in *Control Panel → User Accounts → Credential Manager → Windows Credentials*.

::::
:::::

### File Transfers

File transfers require you to unlock the vault again unless you have chosen to save your vault passphrase in the keychain.

### Renaming

When renaming a vault the behaviour depends on whether the vault is locked or unlocked:
- Renaming a _locked_ vault will rename the vault folder with no changes to the encrypted contents.
- Renaming an _unlocked_ vault changes it to regular folder with decrypted contents.

## Browser

You can open and browse multiple vaults on a server in a single browser window. For each vault to be opened you will be prompted to enter your passphrase to decrypt the filenames. Decrypted filenames when browsing a vault will show a padlock overlay icon.

:::{image} _images/Cryptomator_Vault_Browser.png
:alt: Cryptomator Vault Browser
:width: 600px
:::

### Moving Files Into Vault

You can move files from and to the vault. Because files need to be encrypted or decrypted respectively they pass through your local computer and cannot be moved on the server-side.

:::{attention}
The vault must be unlocked before you move files to it, otherwise the files won't be encrypted.
:::

### Access Vaults on Local Disk

Both [Cyberduck](../cyberduck/index.md) and [Mountain Duck](../mountainduck/index.md) support browsing your local disk to access vaults created on your computer. Refer to the [tutorial](../tutorials/vault_localdisk.md).

## Known Limitations

- As [Name shortening](https://docs.cryptomator.org/en/latest/security/architecture/#name-shortening) is not supported the maximum length for a filename (including extension) is 146 characters. Note that using non-ASCII characters in your filenames may lower this limit.   
- Changing the vault passphrase is currently not supported.
- To delete a vault it cannot be unlocked. Choose *Cancel* in the vault password prompt to skip unlocking the vault after selecting the vault folder for delete.
- Creating or accessing a vault in a vault is currently not supported using Cyberduck.
- Locking or unlocking a vault requires network connectivity using Mountain Duck regardless of the [connect mode](../mountainduck/connect/index.md).

## Preferences

### Auto Detect

Uncheck *Preferences → Cryptomator → Auto detect and open Vault in browser* to disable opening vaults by default when opening the vault directory in the browser.

### Use Keychain

Save the password in Keychain or Credential Manager to unlock vaults automatically upon connecting.

:::{note}
Without saving the vaults passwords using keychain, you will receive passwords prompts for the vaults after reconnecting to the server or cloud storage.
:::

## References

See [Encryption Security Architecture](architecture/index.md).