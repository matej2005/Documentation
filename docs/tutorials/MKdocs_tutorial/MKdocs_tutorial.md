# MKdocs

Pro vytváření dokumentace jsou v momentální době dvě ověřené možnosti. První z nich využívá program MarkText nebo popřípadě jiný WYSIWYG (What You See Is What You Get) markdown file editor dle vaší libosti. Druhá možnost využívá Python virtuální prostředí a VScode a umožní vám simulaci celé DRC-wiki na vašem zařízení pro případné debugování.

Pro psaní "pěknějších" `.md` souborů můžete zkouknout [tento YouTube tutoriál](https://www.youtube.com/watch?v=xlABhbnNrfI) nebo jeho [textovou verzi](https://jameswillett.dev/getting-started-with-material-for-mkdocs/).


## Možnost 1 - MarkText

1. Nejprve si stáhněte a nainstalujte editor `.md` souborů, jako například [MarkText](https://marktext.me/).

2. V něm si vytvořte dokumentaci pro váš projekt/tutoriál.
    ![MarkText HelloWorld](images/Hello_world.png)

3. Poté je třeba náš `.md` soubor vložit do složky s názvem projektu. K němu pak můžeme přidat složku `images`, která bude obsahovat všechny obrázky týkající se daného projektu. 

    !!! info "Průběžná kontrola"
        Nyní zkontrolujte strukturu vašeho projektu. Pokud se všechno povedlo, měla by vypadat zhruba takto:
        ```mermaid
        graph LR
            A["hello_world_project/"] --> B["images/"];
            A --> D["my_first_project.md"];   
        ```

4. Jakmile máte složku hotovou, přejděte na [repozitář DRC-wiki na Githubu](https://github.com/BUT-DRONE-RESEARCH-CENTER/Documentation).
![Homepage DRC-wiki repozitáře](images/repo_home.png)

5. Nyní rozklikněte složku `docs` a v ní pak `projects` nebo `tutorials`.

    > Pro projekty je ještě potřeba vybrat typ projektu `hardware`, `software`, `hybrid`.

6. V menu *Add file* zvolte *Upload files*. 
    ![Zakládání složky projektu](images/project_file_creation.png)

7. Dále stačí přetáhnout celou složku do prohlížeče:
    ![Ukázka nahrávání projektu](images/project_github_upload.png)

8. Do složky s názvem projektu přidáme ještě soubor s *názvem* `.pages` (tedy bez koncovky). 

    > Tento soubor udává pořadí a názvy zobrazovaných `.md` souborů při zobrazování v menu DRC-wiki. 

    !!! warning "Poznámka k obsahu `.pages`"
        Obsah souboru se liší podle toho, zda chceme aby se náš projekt nebo tutoriál zobrazoval jako složka s více stránkami (převážně pro projekty) nebo jako jedna stránka (například tento tutoriál je přímo ve složce tutorials).


=== "Složka `.md` souborů"
    
    Obsah `.pages` souboru pro projekt `Hello_world` by mohl vypadat nějak takto: 
    ```
    nav:
        - Main-Hello world: my_first_project.md
        - ...
    ```
    > Tím říkáme: Zobraz soubor `my_first_project.md` v menu s názvem `Main-Hello world`. 
    Řádek `- ...`, pak říká: Dále zobraz zbylé `.md` soubory.
    
    Vytvoření a nahrání na github:
    ![Ukázka .pages souboru](images/project_pages_file.png)

    > Pak už stačí dát jen *Commit changes...* a máte hotovo
    

=== "Jedna stránka"
    
    Obsah `.pages` souboru pro složky, ve kterých je jen jeden `.md` soubor: 
    ```
    collapse: true
    ```
    > Tím říkáme: Zobraz soubor `my_first_project.md` přímo v menu. 


    !!! info "Jak se teď nastaví název souboru v menu?"
        Defaultně podle prvního nadpisu v souboru. Pokud chcete jméno v menu změnit, vložte na začátek `.md` souboru:
        ```
        title: Název v menu
        ```


Teď už stačí jen zkontrolovat DRC-wiki, která se aktualizuje cca 30 s po nahrání. 

:tada: Gratuluji k nahrání vašeho projektu! Pokud máte potíže, kontaktujte mě s případnými dotazy na 247425@vutbr.cz nebo na discordu pod jménem Ondra[247425].

