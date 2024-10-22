# OpenGL Concepts and Questions

### 1. Ce este un viewport?
Viewport-ul este o regiune dreptunghiulară de pe ecran în care OpenGL redă scena. Practic, este fereastra sau suprafața de vizualizare în care sunt desenate obiectele 3D și se poate seta folosind funcția `GL.Viewport(x, y, width, height)`.

### 2. Ce reprezintă conceptul de frames per second din punctul de vedere al bibliotecii OpenGL?
Frames per second (FPS) reprezintă numărul de cadre (imagini) randate pe secundă de OpenGL. Este o măsură a performanței aplicației grafice și indică cât de rapid poate motorul grafic să redea scena pe ecran. O valoare mai mare a FPS indică o redare mai fluidă a graficii.

### 3. Când este rulată metoda `OnUpdateFrame()`?
Metoda `OnUpdateFrame()` este rulată înainte de fiecare cadru randat, în ciclul de redare. Aceasta este responsabilă cu logica de actualizare a stării jocului sau aplicației (ex. mișcarea obiectelor, calcule de fizică), dar nu efectuează desenarea efectivă pe ecran.

### 4. Ce este modul imediat de randare?
Modul imediat de randare este o modalitate veche în OpenGL de a trimite geometria direct în pipeline-ul grafic. Acesta implică folosirea funcțiilor `GL.Begin()` și `GL.End()`, în cadrul cărora sunt specificate coordonatele și alte proprietăți ale fiecărui vârf al obiectelor. Este un mod mai lent și mai puțin eficient decât metodele moderne de randare (ex. VBO-uri și VAO-uri).

### 5. Care este ultima versiune de OpenGL care acceptă modul imediat?
Modul imediat a fost depreciat începând cu OpenGL 3.0, dar a fost complet eliminat în profilele "core" ale OpenGL începând cu OpenGL 3.1. Versiunile mai recente de OpenGL pot încă folosi modul imediat în profilul de compatibilitate, dar nu este recomandat pentru performanță și eficiență.

### 6. Când este rulată metoda `OnRenderFrame()`?
Metoda `OnRenderFrame()` este rulată după metoda `OnUpdateFrame()`, și este responsabilă cu randarea efectivă a scenei pe ecran. Aici se vor face apeluri OpenGL pentru a desena obiectele și pentru a actualiza buffer-ul grafic.

### 7. De ce este nevoie ca metoda `OnResize()` să fie executată cel puțin o dată?
Metoda `OnResize()` este necesară pentru a ajusta viewport-ul și proiecția atunci când dimensiunea ferestrei se schimbă. Dacă această metodă nu este apelată, obiectele 3D nu vor fi scalate corect sau ar putea fi deformate în cazul în care fereastra este redimensionată.

### 8. Ce reprezintă parametrii metodei `CreatePerspectiveFieldOfView()` și care este domeniul de valori pentru aceștia?
Metoda `CreatePerspectiveFieldOfView()` (în contextul OpenTK sau OpenGL, similar cu `gluPerspective`) creează o matrice de proiecție pentru vizualizarea în perspectivă. Parametrii acestei funcții includ:
- `fieldOfView`: Unghiul câmpului vizual (în radiani), de obicei între 45° și 60° pentru aplicații 3D.
- `aspectRatio`: Raportul între lățimea și înălțimea ferestrei.
- `nearPlane`: Distanța de la cameră până la planul apropiat de tăiere. Obiectele mai apropiate decât această distanță nu vor fi afișate.
- `farPlane`: Distanța până la planul îndepărtat de tăiere. Obiectele mai departe decât această distanță nu vor fi afișate.

Valorile tipice pentru acești parametri:
- `fieldOfView`: 45°-60° (aproximativ 0.785 - 1.047 radiani),
- `aspectRatio`: raportul lățime/înălțime al ferestrei,
- `nearPlane`: 0.1 sau 1.0,
- `farPlane`: câteva sute sau mii de unități, cum ar fi 1000.
