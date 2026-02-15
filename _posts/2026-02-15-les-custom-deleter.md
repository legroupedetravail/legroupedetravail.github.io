---
layout: post
title: Les Custom Deleter
date: 2026-02-15 15:08 +0100
description: Mettre en place un Custom Deleter
image: 
categories: [STL]
tags: Mettre en place un Custom Deleter
author: olc
---
# Les Custom Deleters en C++11

## Introduction

En C++11, les pointeurs intelligents comme `std::unique_ptr` et `std::shared_ptr` ont été introduits pour aider à gérer automatiquement la mémoire et éviter les fuites en respectant le paradigme RAII. Par défaut, ces pointeurs utilisent l'opérateur `delete` pour libérer la mémoire. Cependant, il est parfois nécessaire de personnaliser la manière dont la mémoire est libérée. C'est là que les *custom deleters* entrent en jeu.

Un *custom deleter* est une fonction ou un objet fonctionnel qui est appelé pour libérer une ressource lorsqu'un pointeur intelligent est détruit. Cela peut être utile pour gérer des ressources qui ne sont pas allouées avec `new`, comme des fichiers, des sockets, ou des objets qui nécessitent une méthode spécifique pour être libérés.

## Exemple de Code

Voici un exemple simple montrant comment utiliser un *custom deleter* avec `std::unique_ptr` et la librairie **libmodbus** :

```cpp
#include "pch.h"

int main(int argc, char** argv)
{	
	static constexpr const char* ADDRESS = "127.0.0.1";
	static constexpr const int PORT = 502;

	std::unique_ptr<modbus_t, void(*)(modbus_t*)> modbus(
		modbus_new_tcp(ADDRESS, PORT),
		modbus_free
	);

	return EXIT_SUCCESS;
}
```

Dans cet exemple, nous declarons une connexion modbus TCP/IP par le biais de la fonction `modbus_new_tcp`. Afin de ne pas se risquer d'oublier la libération de la connexion, nous passons comme second argument au constructeur la fonction `modbus_free`.

## Avantages et cas d'utilisation

Les *custom deleters* sont particulièrement utiles dans les situations suivantes :
- Respect du principe RAII ;
- Gestion des ressources autres que la mémoire (par exemple, des fichiers, des connexions réseaux, etc.) ;
- Utilisation de bibliothèque qui nécessitent des méthodes spécifiques pour libérer des ressources ;
- Personnalisation du comportement de nettoyage pour des objets spécifiques.

## Conclusion

Les *custom deleters* en C++11 offrent une grande flexibilité dans les gestion des ressources. Ils permettent de s'assurer que les ressources sont libérées de manière appropriée, même si ces ressources ne sont pas allouées avec new. Cela peut rendre votre code plus sûr et plus facile à maintenir.
