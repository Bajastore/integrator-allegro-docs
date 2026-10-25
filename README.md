# Integrator Allegro

Dokumentacja aplikacji tworzonej na własne potrzeby sprzedawcy BajaStore.

## Przeznaczenie

Integrator łączy lokalny katalog produktów z plików XML hurtowni z obsługą sprzedaży na Allegro. Panel obejmuje produkty, powiązania ofert, reguły cenowe, zamówienia, dokumenty sprzedaży i szablony opisów. Nie jest usługą oferowaną innym sprzedawcom.

## Stan integracji

Aplikacja jest rozwijana. Rejestracja klienta API i wdrożenie autoryzacji stanowią kolejny etap projektu. Nie deklarujemy aktywnej synchronizacji produkcyjnej ani działającej publikacji przez API.

Pierwszy etap po podłączeniu API obejmuje odczyt ofert, ustawień sprzedaży i zamówień oraz weryfikację powiązań istniejących ofert z katalogiem lokalnym.

## Wnioskowane uprawnienia

| Zakres | Zastosowanie |
| --- | --- |
| `allegro:api:sale:offers:read` | Odczyt własnych ofert i porównanie powiązań z katalogiem produktów. |
| `allegro:api:sale:settings:read` | Odczyt ustawień sprzedaży potrzebnych do konfiguracji integracji. |
| `allegro:api:orders:read` | Pobieranie własnych zamówień do obsługi sprzedaży i fakturowania. |

Na tym etapie nie wnioskujemy o uprawnienia do zmiany ofert, zwrotów pieniędzy ani zarządzania reklamami. Istniejąca aplikacja BajaStore AI do analizy Allegro Ads jest osobnym projektem.

## Planowany przebieg połączenia

1. Właściciel uruchamia połączenie konta w panelu Integratora.
2. Loguje się bezpośrednio w Allegro i sprawdza zakres zgody.
3. Allegro przekierowuje do aplikacji w przepływie OAuth Authorization Code.
4. Integrator pobiera dane dopiero po poprawnym zakończeniu autoryzacji.

Obsługa OAuth wymaga wdrożenia i testów przed uruchomieniem. Rejestracja aplikacji sama nie uruchamia pobierania danych.

## Zasady danych i bezpieczeństwa

Dokumentacja publiczna nie zawiera danych klientów, haseł, tokenów ani kodu aplikacji. Dane zamówień mają służyć wyłącznie obsłudze własnej sprzedaży. Docelowe połączenie wymaga bezpiecznego przechowywania sekretów poza repozytorium, walidacji OAuth oraz kontroli dostępu; gotowość tych mechanizmów musi zostać potwierdzona przed uruchomieniem integracji.

## Dalsze etapy

Planowane aktualizacje cen, stanów magazynowych oraz zamykanie i wznawianie ofert wymagają osobnego wdrożenia, testów i odpowiednich uprawnień API. Aktualizacje XML mają zachowywać własne opisy i zdjęcia ofert.

## Kontakt

Pytania dotyczące dokumentacji można kierować przez [zgłoszenia w repozytorium](https://github.com/Bajastore/integrator-allegro-docs/issues). Nie należy zamieszczać tam danych klientów ani danych dostępu.
