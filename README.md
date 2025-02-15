# yama-pls
def read_league_data(self):
    with open(self.league_file, mode='r') as file:
        reader = csv.reader(file)
        league_data = [row for row in reader]
    return league_data

def apply_patch(self, league_data):
    with open(self.patch_file, mode='r') as file:
        reader = csv.reader(file)
        patch_data = [row for row in reader]

    for patch in patch_data:
        for row in league_data:
            if row[0] == patch[0]:  # Takım ismi eşleşirse
                row[1] = patch[1]  # Puanı güncelle
                break

def save_patched_data(self, league_data):
    with open(self.league_file, mode='w', newline='') as file:
        writer = csv.writer(file)
        writer.writerows(league_data)

def patch_league(self):
    league_data = self.read_league_data()
    self.apply_patch(league_data)
    self.save_patched_data(league_data)def read_squad_data(self):
    with open(self.squad_file, mode='r') as file:
        reader = csv.reader(file)
        squad_data = [row for row in reader]
    return squad_data

def apply_patch(self, squad_data):
    with open(self.patch_file, mode='r') as file:
        reader = csv.reader(file)
        patch_data = [row for row in reader]

    for patch in patch_data:
        for row in squad_data:
            if row[0] == patch[0]:  # Takım ismi eşleşirse
                row[1:] = patch[1:]  # Kadroyu güncelle
                break

def save_patched_data(self, squad_data):
    with open(self.squad_file, mode='w', newline='') as file:
        writer = csv.writer(file)
        writer.writerows(squad_data)

def patch_squad(self):
    squad_data = self.read_squad_data()
    self.apply_patch(squad_data)
    self.save_patched_data(squad_data)
