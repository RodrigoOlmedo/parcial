	
	#include <stdlib.h>
	#include<stdio.h>
	#include<string.h>
	typedef struct{
		long int id;
		char descripcion[100];
		int t;
		char m;	
	}p;

	p funcion(long);

	int main()
	{
   		p pri;
   		long id;
   		printf("Bienvenido. Ingrese el id de la pieza:");
   		scanf("%i",&id);
   		pri=funcion(id);
   		if(pri.id==-1){
   			printf("error");
   			return -1;
   		}
   		printf("%l\n%s\%i\n%c\n",&pri.id,&pri.descripcion,&pri.t,&pri.m);
   		return 0;	
	}

	p funcion (long id)
	{
		char aux[100]="Registro Procesado";
		char *d;
		p parcial;
		FILE* fo, *ft;
	
		if((fo=fopen("datos.dat","rb+"))==NULL) 
		{ 
			return parcial;
		}
 		fread(&parcial,sizeof (p), 1, fo);
 		while(!feof(fo))
 		{
			fread(&parcial,sizeof (p), 1, fo);
			if(parcial.id==id)
			{
		  		if(parcial.m=='A')
		  		{
		  			strcpy(parcial.descripcion,aux);
		  			parcial.m=='B';	 
  		  		}
       	  			else
		  		{
		   	 		while(*d)
			  		{
			   			d=parcial.descripcion;
  			   			if(*d=='a'||*d=='o')
			   			{
			   	   			*d='e';
	   		   			}
			   			d++;
 		      			}
		  	  		if((ft=fopen("baja.dat","ab+"))!=NULL)
			  		{
						fwrite(&parcial,sizeof (p), 1, ft);
 			  		}
	   		  		else
			  		{
  	  		    			parcial.id=-1;return parcial;
		      			}
		  		}
  				fwrite(&parcial,sizeof (p), 1, fo);
  				fclose(fo);
  				fclose(ft);
  				return parcial;    
 	    		}
 	    
    		}
    		fclose(fo);
		fclose(ft);
 		printf("no se encontro la pieza");
		parcial.id=-1;return parcial; 	 	 
	}
