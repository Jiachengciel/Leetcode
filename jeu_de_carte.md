 代码：
 ==
    #pragma once
    #include <iostream>

    using namespace std;

    class Carte{

    private:
        int numero;

    public:
        static int nbreDeCartes;
        Carte();
        int getNumero() const;
        virtual void affiche(ostream& s) const=0;
    };

    ostream & operator<<( ostream &s , Carte const & _carte);

    bool carteEstPoint100(Carte* carte);
    bool carteEstPoint50(Carte* carte);