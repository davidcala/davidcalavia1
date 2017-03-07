# davidcalavia1

 django-admin.py, per veure comandes que fa el django
 django-admin.py startproject sobres
 terminal ha destar on quan fem ls surti el manage.py, les dos terminals!!!!
 fem commit de tot
 obrim editor
 manage.py
 manage.py runserver, tenim migracions que no estan aplicades, quina? django ve amb 4 taules de series, i cal fer comando migrate pero poder seguir, podem parar al servidor i fer el migrate o canviar de pestaña i ferho alli. ara ja tenim una bbdd gratis
 servidor desenvolupament es el de proves de la web
 fer un altre cop el runserver
 python manage.py createsuperuser crea i podem entrar a la web amb aquelles dades i veure que hi ha i fer coses per alli(contra 123456 i nom admin)
 python manage.py startapp + nom de la app, no ficar el nom del projecte!!!!!!!!!
 fem commit de la app
 programem models.py, es com la bbdd i aqui es fa amb python no com feiem abans amb sql
 cal anar a settings a activar les coses, anem a installed apps i fiquem isobres, ara ja estara instalada
 hem modificat el model de lapp, cal fer una migracio, li diem a terminal que generi scripts per canviarho python manage.py makemigrations, aixi crea lescript i ara lhem daplicar fent un migrate!
 python manage.py shell, entrem a consola i podem crear un sobre
          from isobres.models import*
          import datetime
          s1 = Sobre(amount=100, date=datetime.date.today(), concept = "Pa Rajoy")
          s1.save()  ho guarda a la bassa de dades
          ara crear un altre sobre no costa res
                    s2 = Sobre(amount=200, date=datetime.date.today(), concept = "Pa Cospedal")
          s2.save()
aixo substitueix treballar amb la bbdd, tot i que es pot fer
tambe es poden fer consultes
  sobres = Sobre.objects.all()
  for s in sobres:
      print s.amount, s.id
i retorna el que li hem demanat

podem fer cerques tambe
     sobres = Sobre.object.get(id=2)
     print sobres.id
per sortir, quit()

admin.py registra els administradors, fiquem a dins lo seguent
admin.site.register(Sobre), sobre diu que no el coneix, doncs from isobres.models import Sobre
ara desde la web podem anar afegint sobres i demes tambe
fer relacions, anem a models
creem la classe Empresa a models i fiquem atributs i imports necessaris per reutilitzar taules
ara caldra tornar a generar migracions i aplicarles
pero abans anem a admin i afegim empresa al import
fem el makemigrations i dona un error, no important, tenim ara claus no nules, fiquem opcio de ficar valors per defecte, ens demanen lidentificar dempresa i fiquem un 1 als 2 casos i ja es podra fer i fem el migrate, podem comprovar el codi que sha generat a un dels fitxers i tambe  a la web 
atencio, classe amb singular i a la bbdd ho fica amb plural!! empresa, empresas sobre i sobres
aqui podem crear empresa i ficar nom i web que son les dades que em dit que tindra
els sobres es vinculen directament a lempresa 1 com ho hem dit abans, igual que amb lusuari 1
creem la funcio unicode a models.py per a que surti de forma diferent a la web, abans sortia empresas object i ara surt el nom de lempresa
views.py, funcio mainpage que reb request
ara a urls.py
^admin el cosa rara fa que hagi de començar aixi, si no estigues i la web fos elmeuadmin tambe hi aniria
[aA]dmin vol dir que sigui admin o Admin, una de les dos
$ el dolar es final de cadena
^admin/$ es lo mateix que ^admin/
pero
^admin/1 sol quadra amb la segona, amb la del dolar no
^$ aixo es cadena buida i totes les cadenes quadren
fem aixo:     url(r'^$', mainpage), i ficar limport corresponent
ara si cridem la pagina sense res mes, anira a la mainpage
