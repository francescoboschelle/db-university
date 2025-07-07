# Universitá:

Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:

- sono presenti diversi `Dipartimenti` (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
- ogni `Dipartimento` offre più `Corsi di Laurea` (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
- ogni `Corso di Laurea` prevede diversi `Corsi` (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
- ogni `Corso` può essere tenuto da diversi `Insegnanti`;
- ogni `Corso` prevede più `appelli d'Esame`;
- ogni `Studente` è iscritto ad un solo `Corso di Laurea`;
- ogni `Studente` può iscriversi a più `appelli di Esame`;
- per ogni `appello d'Esame` a cui lo `Studente` ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente.

## Tabelle

- dipartimenti
  | id | nome |
  | -------- | ------- |
  | BIGINT PK AUTO_INCREMENT | VARCHAR NOTNULL |

- dipartimento_corso_laurea
  | dipartimento_id | corso_laurea_id |
  | -------- | ------- |
  | BIGINT PK | BIGINT PK |

- corsi_laurea
  | id | nome |
  | -------- | ------- |
  | BIGINT PK AUTO_INCREMENT | VARCHAR NOTNULL |

- studenti
  | id | nome | cognome | corso_laurea_id |
  | -------- | ------- | ------- | ------- |
  | BIGINT PK AUTO_INCREMENT | VARCHAR NOTNULL | VARCHAR NOTNULL | BIGINT NOTNULL |

- corsi
  | id | corso_laurea_id | nome |
  | ------- | ------- | ------- |
  | BIGINT PK AUTO_INCREMENT | BIGINT NOTNULL | VARCHAR NOTNULL |

- studenti_appelli
  | dipartimento_id | corso_laurea_id | voto |
  | -------- | ------- | ------- |
  | BIGINT PK | BIGINT PK | TINYINT NULL |

- insegnanti
  | id | nome | cognome |
  | -------- | ------- | ------- |
  | BIGINT PK AUTO_INCREMENT | VARCHAR NOTNULL | VARCHAR NOTNULL |

- insegnante_corso
  | insegnante_id | corso_id |
  | -------- | ------- |
  | BIGINT PK | BIGINT PK |

- appelli
  | id | corso_id | nome | data | cfu |
  | -------- | ------- | ------- | ------- | ------- |
  | BIGINT PK AUTO_INCREMENT | BIGINT NOTNULL | VARCHAR NOTNULL | DATE NOTNULL | TINYINT NULL |
