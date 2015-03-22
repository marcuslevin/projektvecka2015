Instruktioner för att förbereda din mac för att utveckla i ruby

## 1 Installera Homebrew ##

Homebrew är en pakethanterare, det vill säga ett program som används för att hämta, kompilera, och installera program.

1. Starta terminalen
2. Hämta och installera homebrew: `ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"`
3. Skriv in ditt lösenord för datorn (inget kommer synas på skärmen) och tryck på enter

### 1.1 Installera X-Code Command Line Tools ###

Om ett fönster dyker upp och ber dig installera Xcode Command Line Tools, klicka på `Install`.

Om det inte dyker upp, skriv `xcode-select --install`

När Xcode Command Line Tools installerats klart, markera kommandopromptsfönstret och tryck på `enter`.

### 1.2 brew doctor ###

När installationen är klar, kör `brew doctor`.

Det kan dyka upp ett par varningar. Följande varningar är normala:

	* Outdated version of /usr/bin/install_name_tool
	* Git could not be found in your path
	* No developer tools installed

Oavsett om fu fått några varningar eller inte, ska du fortsätta med följande steg.

### 1.3 Installera git ###

Git är ett versionshanteringssystem som används av bl.a. homebrew.

Skriv `brew install git`

Git kan ge en varning, ignorera den, vi fixar den lite senare.

## 2 Byt shell till zsh ##

I terminalen kan man köra olika "shells". Som standard i OS X kör man bash. Vi kommer byta till zsh; ett shell med mer funktionalitet.

### 2.1 Installera wget ###

wget är ett program som gör det enkelt att ladda ner filer från Internet utan att använda en webbläsare

Skriv `brew install wget`

### 2.2 Installera oh-my-zsh ###

oh-my-zsh är ett paket med bra inställningar för zsh.

1. klistra in `wget --no-check-certificate https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh`
2. Skriv in ditt lösenord för datorn (inget kommer synas på skärmen) och tryck på `enter`.
3. Döda terminalen: `cmd Q`.
4. Starta terminalen igen.
5. Klistra in `echo export PATH='/usr/local/bin:$PATH' >> ~/.zshrc`
6. Döda terminalen (`cmd Q`) igen.
7. Starta terminalen igen.
8. Njut av zsh.


## 3 Installera rbenv och ruby-build

rbenv är ett program som låter dig köra olika versioner av ruby i olika projekt. ruby-build är ett program som hämtar och kompilerar olika versioner av ruby.

1. Skriv `brew install rbenv ruby-build`
2. Vänta medan programmen laddas ner och installeras

### 3.1 Konfigurera din terminal att använda rbenv ###

1. Navigera till din hemkatalog: `cd ~`
2. Öppna konfigurationsfilen för zsh i nano: `nano .zshrc`
3. Sist i filen, klistra in `eval "$(rbenv init -)"`
4. Spara filen: `ctrl x` och tryck på y och sen enter
5. Döda terminalen `cmd Q` och starta den igen
6. Dubbelkolla att rbenv är korrekt installerat: `type rbenv` (datorn bör svara `rbenv is a shell function`)

## 4 Installera ny ruby-version ##

1. Skriv `rbenv install 2.1.0`
2. Vänta medan ruby hämtas och kompileras
3. Gör 2.1.0 till standardruby på din dator: `rbenv global 2.1.0`
4. Döda terminalen `cmd Q` och starta den igen
5. Dubbelkolla att rätt version av ruby används: `ruby -v` (datorn bör svara något liknande `ruby 2.1.0p0` )

### 4.1 Installera bundler ###

Bundler används för att lätt installera olika ruby-bibliotek, så kallade gems.

1. Installera bundler: `gem install bundler`
2. Uppdatera kommandoprompten så den hittar bundler: `rbenv rehash`
3. Dubbelkolla att kommandoprompten hittar bundler: `which bundler` (datorn bör svara med en sökväg liknande `/Users/daniel.berg/.rbenv/shims/bundler`)


