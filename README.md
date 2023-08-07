download_Incra
Download parcelas, limites e memorial do site do incra automaticamente
####import requests

def download_file(url, local_filename):
    with requests.get(url, stream=True) as response:
        response.raise_for_status()
        with open(local_filename, 'wb') as file:
            for chunk in response.iter_content(chunk_size=8192):
                file.write(chunk)

if __name__ == "__main__":
    url = "https://example.com/image.jpg"  # Substitua pela URL do arquivo que deseja baixar
    nome_do_arquivo_local = "imagem_baixada.jpg"  # Substitua pelo nome que deseja salvar localmente

    try:
        download_file(url, nome_do_arquivo_local)
        print("Download concluído!")
    except requests.exceptions.RequestException as e:
        print(f"Erro durante o download: {e}")
####
